---
title: "Proxy Automatic Configuration file"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by JFire on 2008-03-07
Hello

I have written a small Proxy Automatic Configuration file for myself so when I move my laptop from home, to work or when I invoke local proxy servers my applications will automatically use the correct proxy. 

This works very well with Opera and Firefox.

But I am having trouble getting it to work with Ubuntu's 'Network Proxy'. (System->Preferences->Network Proxy)

Here is my PAC file:

> cat /home/jack/ProxyAutoConfig.pac
function FindProxyForURL(url, host)
{
return "PROXY 127.0.0.1:8080; DIRECT; PROXY proxy.workproxy:8080";
}

I suspect that the issue may lie with the fact that 'Network Proxy' wants an URL for the the location of the file, but the file is located within my home directory.

I have tried both my Opera and Firefox methods for pointing to the file, but alas this doesn't seem to work.

Opera: "/home/jack/ProxyAutoConfig.pac"
Firefox: "file:///home/jack/ProxyAutoConfig.pac"

Can anyone tell me what I'm doing wrong, or if there's a way around this 'without' having to put the file online somewhere.](*,)

Thanks:popcorn:

---

### Post by koenn on 2008-03-07
an obvious workaround would be to install the smallest web server you can find on your laptop and let it serve up the pac file, so you can refer to it with a url.
Proxy Auto Configuration is meant for centralized management of networked hosts, especially web browsers, so it's not that strange that the expected format is a URL. 

lighttpd is a lightweight web server, but maybe thare are even smaller ones. 

Side Note : 
if you're any good at javascript, you could probably put a test in that pac to figure out what network you're on, and assign a suitable proxy accordingly. 
As it is, you seem to be using "try this proxy, and if it fails, try the next one" approach.

---

### Post by JFire on 2008-03-07
I have installed lighttpd and I belive I have configured it appropriately. My file is now accessible via "http://localhost/Test.pac" and I have edited "/etc/lighttpd/lighttpd.conf" to explicitly set the .pac MIME type to "application/x-ns-proxy-autoconfig".

Then I've set the ProxyAutoConfiguration URLs for Opera, Firefox and Gnome, to point to "http://localhost/Test.pac"

The results are that the browsers work, but my Gnome Apps do not. So back to square one. For testing purposes, I have simplified the ProxyAutoConfig file to this:

jack@jack-laptop:~$ cat /home/www/Test.pac
function FindProxyForURL(url, host)
{
return "DIRECT";
}

By the way, to test that the Gnome proxy is working, I use the "Weather Report 2.20" desktop panel application. This seems to work fine when the setting Gnome's Network Proxy manually, but not when using a PAC file. In order to eliminate the possibility that it might just be this one application that doesn't play well with the Proxy Autoconfiguration Settings, could someone suggest another application that I can use to test with? Thanks.

---

### Post by JFire on 2008-03-07
Urg... I should have done this at the start. Oh well.

So, I took my own advice and tried to test some different Gnome applications to see if they worked. They didn't. But the 'Synaptic Package Manger' _did_ give me an extra hint as to where the problem was.

It seems that for the Autoconfiguration URL to work at all, all other fields in the Network Proxy settings HAVE to be blank, not simply greyed out.

So, the solution was to enable the Manual proxy settings, then delete all enteries. Close 'Network Proxy' then start it again and set it to use the Autoconfiguration URL.

It seems that this is a bug in the way that Network Proxy behaves when greying out setting sand actually setting proxy settings.

So, just incase anyone is interested. A web server is not required after all. Just pointing to the file location will work. Thanks for the help tho, it was kind of fun playing with the web server.\\:D/

Now, to file a bug report...:???:

---

### Post by koenn on 2008-03-08
thanks for the feedback, it's good to know.

---

