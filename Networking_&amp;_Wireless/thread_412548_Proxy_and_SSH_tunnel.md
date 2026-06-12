---
title: "Proxy and SSH tunnel"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by kokomo_35 on 2007-04-18
Hello !

I am trying to bypass my office's proxy using an SSH tunnel for HTTP and FTP connections.

I have no problem making a SOCKS proxy and using it with Firefox :
ssh -D 8080 thomas@my-ubuntu
I don't know exactly what SOCKS is. What I understand, is that requests to the port number 8080 are forwarded to my machine through an SSH tunnel. What I DON'T understand is how can my computer know that it has to forward these requests on the net and bring me back the responses.
I have read that we can use tsock for many applications such as apt-get.
But what I want to do is to define an HTTP and FTP proxy through SSH.
I have tried :
ssh -L 8080:my-ubuntu:80 thomas@my-ubuntu
It does not work...
The connection is well established (sshd.log).
Same question: how can my computer know what to do?

Thanks in advance for your help.

Regards,

Thomas

---

### Post by Sencer on 2007-04-18
> **kokomo_35 said:**
> What I understand, is that requests to the port number 8080 are forwarded to my machine through an SSH tunnel.

Yes. Recent versions of the openssh-server include the ability to act as a socks-server, so it's become as easy to use as you described above. At least with applciations that allow you to set socks proxies.

>  What I DON'T understand is how can my computer know that it has to forward these requests on the net and bring me back the responses.

It's on a per application basis. If the app does not allow you to configure a socks proxy, you can use "tsocks" to trick other applications into using the socks proxy, this happens because tsocks sits on a lower layer and "catches" all connection requests and makes sure they go through the socks proxy. tsocks works fine for almost all applications, you simply configure tsocks correctly, and then start each applications with "tsocks appname".

> But what I want to do is to define an HTTP and FTP proxy through SSH.

openssh does not have an http-proxy, only a socks proxy. The two work on different levels, but if you have socks working, there is really no need for an http proxy. What is it in the end that you are trying to achieve? You said you already have Firefox working with the socks-settings, right?

---

