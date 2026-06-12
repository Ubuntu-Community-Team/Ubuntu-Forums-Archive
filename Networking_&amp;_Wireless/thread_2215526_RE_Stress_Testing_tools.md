---
title: "RE: Stress Testing tools"
date: 2014-04-07
forum: Networking &amp; Wireless
---

### Post by sramm9 on 2014-04-07
hai

hope someone can assist me, i need a tool to help me to do some stress testing for my application running on **_*UBuntu 10.04,    Tomcat 6 ,     MYSQl*_**.
i found this _***JMeter***_ , seem good from what i read on web. But cant find details on how to install them.....

does anyone have ideas ? Please share,,, thank you and have a nice day

---

### Post by glinius on 2014-04-23
JMeter is free and open source tool. It's available from Ubuntu repositories, just "apt-get install jmeter" will help you to install it. If your client OS is different you can download it from [Apache website]("http://jmeter.apache.org/download_jmeter.cgi") and just unpack to suitable location. 

Mention that JMeter is a pure Java application so you'll need to have Java installed (it's recommended to use Oracle JDK 6+) to be able to run it. 

JMeter provides record-and-replay possibility so you will be able to quickly get started by creating JMeter scripts from browser. See [JMeter Proxy Step by Step]("http://jmeter.apache.org/usermanual/jmeter_proxy_step_by_step.pdf") official guide on how to configure JMeter and browser. 

Another possibility for recording JMeter scripts is using [Google Chrome extension]("https://chrome.google.com/webstore/detail/blazemeter-the-load-testi/mbopgmdnpcbohhpnfglgohlbhfongabi?hl=en"). In this case you won't need to worry about proxies, certificates, headers, etc. 

Once you record your test case you will be able to replay it with high number of virtual users. 

Hope this helps,

D.

---

