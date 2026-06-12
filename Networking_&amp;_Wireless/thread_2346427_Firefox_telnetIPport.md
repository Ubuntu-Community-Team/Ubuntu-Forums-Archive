---
title: "Firefox telnet://IP:port"
date: 2016-12-14
forum: Networking &amp; Wireless
---

### Post by nabz0r on 2016-12-14
Hi,

Is there an easy way to open [noparse]telnet:port[/noparse] directly in Ubuntu terminal or putty client from Firefox?
I have purchased CCIE labs from Cisco and I'd love to open them in a local terminal, SecureCRT or Putty (i'd prefer local terminal), and I can achieve this Mac and Windows but it doesn't work in Linux or probably I don't know how to.

Thanks in advanced!

---

### Post by SeijiSensei on 2016-12-14
Are you asking about using telnet as a client or as a server?  Ubuntu comes with the client side telnet program by default.  Just use
```
telnet server port
```
e.g., 
```
telnet mail.example.com 25
```
connects to the SMTP port on mail.example.com.  You can use an IP address for "server" as well.

Hardly anyone ships the telnetd server any more because it is insecure and has been replaced by SSH.

---

### Post by TheFu on 2016-12-14
Really should use ssh instead, but if you need telnet, and there are times where it is handy. then 
```
$ telnet {hostname/IP} {port}
```
is the way.  I only mention this since you are probably someone who would find it useful - there are help pages for every command on Unix-like systems (usually).  You can search the summary using **apropos**  - so **apropos telnet** returns:
```
telnet (1)           - user interface to the TELNET protocol
telnet.netkit (1)    - user interface to the TELNET protocol

```
Those are manpages to get more details.  **man telnet** or **man telnet.netkit** are full of information. Works for 95+% of all commands.  Hope I don't get banned for this.

Why ask the same question twice?

---

### Post by nabz0r on 2016-12-15
Thank you both for the response!
I think you both have misunderstood med here. These labs are accessible on telnet on purpose.

Let me explain a little more how it works. After you login to Cisco account you then go to your labs (separate window and login), access the lab and after clicking on a device to console access, this step in Linux the web browser should be able to open it in a terminal/securecrt or putty but it doesn't it open in another page with the telnet:ip:port and blank page and I want to do is to redirect that page to a terminal.

As I said before it works very well in Mac in both the local terminal and securecrt, in windows I need to install Cisco's putty version which is NOT available for Linux.

I hope this clarifies it a little bit on what I want to do.

---

### Post by TheFu on 2016-12-15
> **nabz0r said:**
>  
I think you both have misunderstood med here.

Yes. And I still don't understand.  Launching an external program from inside a web browser would seem to be a huge security issue. This is why we disable Flash and Java programs launched by browsers. Security.  Or am I completely missing the way it works? Perhaps there is a youtube video showing it?

A few guys in my LUG have been struggling to use Cicso-provided learning tools. Think that most ended up running them inside a VM using OS images provided by cisco.

---

### Post by SeijiSensei on 2016-12-15
What happens if you type [telnet://server:port](telnet://server:port) into the Firefox address bar?  On my Kubuntu machine I get prompted to run the KDE Telnet Service which opens a terminal window pointing to the remote telnet server.

---

### Post by nabz0r on 2016-12-15
> **TheFu said:**
> Yes. And I still don't understand.  Launching an  external program from inside a web browser would seem to be a huge  security issue. This is why we disable Flash and Java programs launched  by browsers. Security.  Or am I completely missing the way it works?  Perhaps there is a youtube video showing it?

A few guys in my LUG have been struggling to use Cicso-provided learning  tools. Think that most ended up running them inside a VM using OS  images provided by cisco.

I could take the config from the routers and re-create them inside a  vm with gns3 but I don't think it will work properly. These are  provided and accessed online and I don't know why Cisco haven't thought  about this. It surely is very easy fix.

> **SeijiSensei said:**
> What happens if you type [telnet://server:razz:ort]("telnet://server:port")  into the Firefox address bar?  On my Kubuntu machine I get prompted to  run the KDE Telnet Service which opens a terminal window pointing to the  remote telnet server.
This is exactly what I want to achieve. After clicking for console access I want Firefox to prompt to run telnet service to open in a terminal, but it doesn't. I get 

```

"This address wasn't understood"
Firefox doesn&#8217;t know how to open this address, because one of the following protocols (telnet) isn&#8217;t associated with any program or is not allowed in this context.
You might need to install other software to open this address.
```

---

### Post by bobnn on 2016-12-16
Plugging that error into google led to to a link that led to this:

[http://ccielab.ro/2009/11/telnet-handler-in-firefox-kubuntu/](http://ccielab.ro/2009/11/telnet-handler-in-firefox-kubuntu/)

From that page:

> First thing to do is to tell Firefox that we WANT to use telnet:// links. To do that we must open Firefox and type &#8220;about:config&#8221; in address bar. And we create a new boolean preference (right click on an empty space), name it &#8220;network.protocol-handler.expose.telnet&#8221; and set the value &#8220;false&#8221; and restart the browser. That should be enough for Firefox to let us select an external application to open &#8220;[telnet://&#8221;](telnet://&#8221;) links.

More there on how to tailor it if you want it to do telnet in a terminal window, which may be best.  I tried installing putty and lcrt and pointing at those, but they didn't work right.

Using the script for gnome-terminal did work.

---

### Post by nabz0r on 2016-12-18
> **bobnn said:**
> Plugging that error into google led to to a link that led to this:

[http://ccielab.ro/2009/11/telnet-handler-in-firefox-kubuntu/](http://ccielab.ro/2009/11/telnet-handler-in-firefox-kubuntu/)

From that page:



More there on how to tailor it if you want it to do telnet in a terminal window, which may be best.  I tried installing putty and lcrt and pointing at those, but they didn't work right.

Using the script for gnome-terminal did work.

I actually have looked at that script before I post here, and obviously  it didn't work for me. How did you do it? I'd really appreciate it if  you share how did it.

Here is the scrip as you see I tried it with gnome-terminal and the permission.

```

#!/bin/sh

address=`echo ${*##telnet://} | sed 's/:/ /g'`

#For xterm junkies :
#xterm -e "telnet $address"

#For gnome-terminal users :
#uncomment the next line but comment
#all other terminal launchers (xterm, konsole)
gnome-terminal -e "telnet $address"

#For konsole hipsters :
#konsole sends args separately to command so we use "" only for telnet
#uncomment the next line but comment
#all other terminal launchers (gnome-terminal, xterm)
#konsole -e "telnet" $address

```

-rwxrwxr-x 1 walwar walwar  474 dec 15 16:37 telnet*

---

