# fluentd-syslog-haproxy-plugin
An logfile haproxy http log parser

## Usage

This plugins works with default http log format from HAProxy:

```
  log-format "%ci:%cp [%tr] %ft %b/%s %TR/%Tw/%Tc/%Tr/%Ta %ST %B %CC %CS %tsc %ac/%fc/%bc/%sc/%rc %sq/%bq %hr %hs %{+Q}r"
```

## Installing steps

```
gem build fluentd-logfile-haproxy-parser.gemspec
fluent-gem install fluentd-logfile-haproxy-parser-0.0.1.gem

```

## Full fluentd configuration

```
<source>
  @type tail
  path <path>/haproxy.log
  pos_file <path>/pos/haproxy.pos
  read_from_head true
  <parse>
    @type haproxy_logfile
  </parse>
  tag haproxy
</source>

<match **>
  @type stdout
</match>
```
