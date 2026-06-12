---
title: "Howto: Dynamic port forwarding and secure proxy with SSH"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by sammydee on 2007-12-04
Hi all.

The aim of this Howto is to explain to someone how they can set up dynamic port forwarding through ssh with minimal technical knowhow.

You may have heard of and used static port forwarding with ssh. Static port forwarding allows you to forward all traffic directed at localhost on a particular port, over a secure ssh session, through the ssh server pc on that port, to a specified host.

This is extremely useful for tunnelling insecure traffic over an open channel, eg for tunnelling VNC like this: [http://ubuntuforums.org/showthread.php?t=220747](http://ubuntuforums.org/showthread.php?t=220747)

Actually there's an easier (but less neat) way of doing the above - ssh into your target machine with the -X option and just type:

> xvnc4viewer 127.0.0.1

Easy! This method actually can be used as a crude proxy, by opening firefox on the remote host and browsing through that, however, it's slow and not really very neat so there is a better way.

Static port forwarding with SSH allows you to forward connections on a case-by-case basis. However, if you want to use a ssh server as a remote proxy, this clearly isn't really what you need.

Dynamic port forwarding allows an ssh client to run a SOCKS proxy on localhost, which allows arbitrary port forwarding to any internet server through the remote ssh server. It looks a bit like this:

Client machine sends http request to localhost SOCKS proxy (ssh client)
ssh client forwards the request to the remote ssh host
Remote ssh host forwards request to the appropriate server.

This can be incredibly useful if you are, for example, in a cafe with unencrypted wireless, but want to keep your traffic more secure by routing it through a remote proxy via ssh. Another potentially useful application is secure home wireless EVEN IF you only have WEP available. Simply connect the wireless router to a network card on the hostpc, and set up the firewall on the host pc to only allow connections on the ssh port. Then you can securely use the WEP network to access the internet through ssh whilst any malicious user can neither use your internet connection, nor sniff your traffic. This is important because there are still a lot of linux drivers for wireless cards that only support WEP.

Here's how to do it:

First I am assuming you have an ssh client on clientpc and an ssh server on hostpc. I am also assuming both servers are running stock Ubuntu 7.10 configurations. You can install the server by running:

```
sudo aptitude install openssh-server
``` on hostpc.

I believe that ubuntu comes with an ssh client as standard, so you shouldn't have to install that on clientpc.

Now SSH is pretty secure to start with, however, you may want to change the standard port to something more obscure to reduce the number of brute force attacks, or even change to certificate only authentication. That's out of the scope of this guide however, so I'll assume you're using standard password authentication and an the standard port 22. One thing that I will STRONGLY recommend is, on hostpc:

```
gksudo gedit /etc/ssh/sshd_config
```

Find

```
PermitRootLogin yes
```

And change it to

```
PermitRootLogin no
```

If you need root access, you can sudo once you're in.

The configuration on clientpc does not need to be changed.

You MUST make sure that any firewalls or internet routers between hostpc and the internet explicitly allow incoming port 22 (or whatever port you decided to use for ssh) connections. This can be a major cause for headaches when troubleshooting and you always feel like an idiot when you find out it was your firewall the whole time :) . When you've done this you can test it by opening an ssh connection to hostpc from clientpc and making sure it all works ok. You can do that with this command:

```
ssh -p yourport -X user@hostpc
```

Where yourport is the port you use for ssh and the -X option allows X forwarding. A neat little trick you can do is, once you have executed the above command and are logged into hostpc, to run:

```
firefox --no-remote
```

This opens a remote instance of firefox displayed on clientpc. Any connections made through this firefox window will originate from hostpc. That's a VERY simple proxy server - cool huh? Might be a bit slow though, over a slower connection, so we'll carry on with the SOCKS proxy method.

You CAN start a dynamic forwarding service on port 9999 by running the following command on clientpc:

```
ssh -p yourport -D 9999 user@hostpc
```

This will start a SOCKS proxy that listens on localhost:9999 and forwards all requests to remotepc. However, I much prefer to do it with a gui that easily allows you to start, stop and modify remote connections. I use gstm which is a great little gtk program for managing ssh port forwards. On clientpc:

```
sudo aptitude install gstm
```

Now open gstm. Click add. Type a name for your tunnel. In this guide, I will call it SOCKS. Fill in all the fields

Login: put the username you use to login to hostpc.
Host: put the ip address or dns name of hostpc. Bear in mind that the ip address you use within your LAN (if you have one) will be different to your remote ip address.
Port you can change which port it connects to hostpc on, if you are using a non-standard ssh port.
You only need to put something for privkey if you know what you are doing. Otherwise you can leave it blank.
If you want to start the tunnel as soon as gstm fires up, you can click the autostart checkbox. 

Now click add.

Type is dynamic.
Port is the port you would like your proxy server on localhost to listen on. I will use 9999

Then click ok. You can start the proxy server listeningt by going into the main gstm menu and clicking on SOCKS, then clicking start. With a bit of luck, it should report that the port forward was successfully set up.

Now all you have to do is configure your applications to use a SOCKS5 proxy on localhost port 9999 and they will magically forward all traffic through this proxy!

While you can of course do this with any application, perhaps the most useful applications to do this with are firefox and pidgin, so malicious eavesdroppers can't sniff your private conversations or web browsing.

For pidgin, it's easy to make it use a proxy. Go to accounts, and select your account then edit account. Click on the advanced tab. Go to proxy type and select SOCKS5, with ip address 127.0.0.1 and port 9999. Of course you can also tell it to use the GNOME proxy settings, and adjust those instead in system/preferences/network proxy.

For firefox, go to edit/preferences. Click the advanced tab. Click settings. Click manual proxy configuration and enter the proxy details.

That's the hard way of doing it. I like to use a plugin called foxyproxy, available here: [http://foxyproxy.mozdev.org/](http://foxyproxy.mozdev.org/)

Enter your proxy information into foxyproxy and you can change it easily at any time by clicking on the foxyproxy text on the bottom right of the firefox window. This makes it trivial to enable secure forwarded internet access at any time in firefox and to disable it again - very useful for laptops and cafe wireless. You can test this by disabling the proxy and visiting [www.whatismyip.org](www.whatismyip.org). then enable it and visit the same address. If the proxy is working, it will show two different ip addresses - cool huh?

That's it! Easy wasn't it? Now whenever you are stuck somewhere with only open wireless, you can still ensure your traffic remains relatively secure! SSH is capable of all sorts of incredible magic things, this is just one aspect of it. I strongly encourage you to research the other uses of it, it's the most useful linux software I have ever used.

If anybody has any problems with this howto, please post here and I'll try and help. Good luck and happy secure browsing!

Sam

---

