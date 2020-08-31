我是光年实验室高级招聘经理。
我在github上访问了你的开源项目，你的代码超赞。你最近有没有在看工作机会，我们在招软件开发工程师，拉钩和BOSS等招聘网站也发布了相关岗位，有公司和职位的详细信息。
我们公司在杭州，业务主要做流量增长，是很多大型互联网公司的流量顾问。公司弹性工作制，福利齐全，发展潜力大，良好的办公环境和学习氛围。
公司官网是http://www.gnlab.com,公司地址是杭州市西湖区古墩路紫金广场B座，若你感兴趣，欢迎与我联系，
电话是0571-88839161，手机号：18668131388，微信号：echo 'bGhsaGxoMTEyNAo='|base64 -D ,静待佳音。如有打扰，还请见谅，祝生活愉快工作顺利。

# Prometheus Mesos Exporter
Exporter for Mesos master and agent metrics

## Installing
```sh
$ go get github.com/mesosphere/mesos-exporter
```

## Using
The Mesos Exporter can either expose cluster wide metrics from a master or task
metrics from an agent.

```sh
Usage of mesos-exporter:
  -addr string
        Address to listen on (default ":9110")
  -exportedSlaveAttributes string
        Comma-separated list of slave attributes to include in the corresponding metric
  -exportedTaskLabels string
        Comma-separated list of task labels to include in the corresponding metric
  -ignoreCompletedFrameworkTasks
        Don't export task_state_time metric
  -master string
        Expose metrics from master running on this URL
  -slave string
        Expose metrics from slave running on this URL
  -timeout duration
        Master polling timeout (default 5s)
  -trustedCerts string
        Comma-separated list of certificates (.pem files) trusted for requests to
        Mesos endpoints
```
When using HTTP authentication, the following values are read from the environment:
- `MESOS_EXPORTER_USERNAME`
- `MESOS_EXPORTER_PASSWORD`

---

Usually you would run one exporter with `-master` pointing to the current
leader and one exporter for each slave with `-slave` pointing to it. In
a default Mesos / DC/OS setup, you should be able to run the mesos-exporter
like this:

- Master: `mesos-exporter -master http://leader.mesos:5050`
- Agent: `mesos-exporter -slave http://localhost:5051`
