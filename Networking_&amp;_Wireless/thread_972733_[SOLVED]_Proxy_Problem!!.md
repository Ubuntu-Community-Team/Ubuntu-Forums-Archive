---
title: "[SOLVED] Proxy Problem!!"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by waynema on 2008-11-06
proxy settings in gnome-network-preferences doesn't apply

I just updated to Intrepid from Hardy. This problem suddenly appears :(

I want to use a global proxy for my system to access internet.
However, in GUI gnome-network-preferences, after setting server AND authentication and pressing "Apply System-Wide..."

the http_proxy env is set right with IP&port, but WITHOUT user & passwd, like:

$ echo $http_proxy
[http://123.123.123.123:123/](http://123.123.123.123:123/)

the correct one should be like: [http://user:passwd@123.123.123.123:123/](http://user:passwd@123.123.123.123:123/)

I already checked the bug here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/271108](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/271108)

Problem above looks similar to mine, but solution doesn't work in my case.

I'm using:
gnome-control-center 1:2.24.0.1-0ubuntu7

Any idea would be great. Thanks in advance:)

---

### Post by chran on 2008-11-06
I had the same issue with ubuntu 8.10 - using proxy at work, direct connection at home.

Setting up proxy via System > Preferences > Network Proxy works globally (no separate settings required at Terminal or Firefox) once. When I'm at home and turned network proxy off, aptitude/ synaptic still keep the proxy settings.

The fix is to manually update proxy settings in:
1) firefox network preferences
2) teminal/ command line - blanks http proxy:
   ```
export http_proxy=
```

Note that there's no space after the '=' sign. To check your current terminal's proxy settings use:
```
echo $http_proxy
```

to restore proxy back use:
```
export http_proxy=http://[username]:[password]@[proxyserverlocation]:[portnumber]/
```

For the security minded, the above will show your proxy username/password when listing history. Feel free to put it in a script or alias in .bashrc

Hope this helps :D

---

### Post by waynema on 2008-11-07
thanks, chran, that surely works :)

And in addition, I want to know WHY that problem appears..

That problem appears on my workstation, which runs hardy for half a year.
However, on my laptop, I directly install 8.04.1 and after updating to the 8.10, no such problem appears. 

I just wonder what set these "http_proxy" "https_proxy" "ftp_proxy" for my gnome-terminal.

---

### Post by chran on 2008-11-07
No probs. Glad it works for you too.

> **waynema said:**
> I want to know WHY that problem appears..
I'd like to know that too :). I suspect with 8.10 the developers are trying to have a central location for proxy configuration (like in Windows/ Mac OS) which doesn't work as seamless as it should be. Traditionally linux comes from command-line - in which http_proxy is a variable. I don't know much about the inner-workings of gnome and can't say where it stores the proxy settings - I always set command-line proxy and firefox separately prior to 8.10 so I'm aware of the above workaround.

I believe the global network proxy works when you install/ upgrade to 8.10 (8.04 to 8.10 in my case) but breaks when you upgrade it (eg. aptitude safe-upgrade). Maybe one of the newer packages is buggy.

---

### Post by waynema on 2008-11-08
Solution Found :)

I found that the gnome-terminal always has configuration from the /etc/apt/apt.conf. And I have set http/ftp/https proxy in that file:

Acquire::http::proxy "http://123.123.123.123:123/";
Acquire::ftp::proxy "ftp://123.123.123.123:123/";
Acquire::https::proxy "https://123.123.123.123:123/";

After deleting these content in apt.conf, the gnome-control-center's setting applies in my gnome-terminal, haha :)

---

### Post by waynema on 2008-11-08
> **chran said:**
> 
Setting up proxy via System > Preferences > Network Proxy works globally (no separate settings required at Terminal or Firefox) once. When I'm at home and turned network proxy off, aptitude/ synaptic still keep the proxy settings.


chran, I think checking the /etc/apt/apt.conf might help your problem. Hope it works for you :)

---

### Post by chran on 2008-11-09
thanks waynema. i know about /etc/apt/apt.conf - mine was blank when my proxy played up. i guess it's not a big deal since there's always $http_proxy workaround.

---

### Post by avessalom on 2008-11-12
> **chran said:**
> 
2) teminal/ command line - blanks http proxy:
   ```
export http_proxy=
```

Note that there's no space after the '=' sign. To check your current terminal's proxy settings use:
```
echo $http_proxy
```

to restore proxy back use:
```
export http_proxy=http://[username]:[password]@[proxyserverlocation]:[portnumber]/
```



better unset the variable:
```
unset http_proxy
```
I had a problem with a zero $http_proxy

---

### Post by Gumm on 2008-11-14
I created a little script that keeps my env.var http_proxy, and the Gnome proxy settings in sync, and also asks me where I am when I log in. This way I select it once, and then that's it for that session.

To create a little scrip that sets your proxy depending on where you log into gtk, do the following:
This script is launched from a very nice little applet called gmessage, so get that:

```
sudo apt-get install gmessage
```

Our scrip will be available for all users using the graphical login, so it will live here at /etc/xprofile
To edit it:

```
gksudo gedit /etc/xprofile
```

Copy the text below, and past it in this file. This scrip sets proxy (and authentication) like so:
Proxy address : 192.168.0.1
Proxy port : 1234
User name : your.name
Password :password
and you would need to edit it with your own detail.

```
#!/bin/sh


gmessage -title "Proxy Select"				\
	-buttons "Home:101,Work:102,GTK_STOCK_CLOSE:103" 	\
	-center 					\
	-geometry "300x100"         			\
	-timeout "5"					\
	-fg "#255261"       				\
        -bg "#C1B5B5"       				\
	"Where are you?"

action=$?
case $action in
101)
	gconftool-2 --set /system/proxy/mode --type string none
	gconftool-2 --set /system/http_proxy/use_http_proxy --type bool false
	unset http_proxy
	gmessage -title "Proxy Select"				\
		-buttons GTK_STOCK_CLOSE       			\
		-center 					\
		-geometry "300x100"         			\
		-timeout "1"					\
		-fg "#255261"       				\
       		-bg "#C1B5B5"       				\
		"No proxy set. Direct internet connection"
	;;
102) 
	gconftool-2 --set /system/proxy/mode --type string manual
	gconftool-2 --set /system/http_proxy/use_http_proxy --type bool true
	export http_proxy=http://username:password@192.168.0.1:1234
	gmessage -title "Proxy Select"				\
		-center 					\
		-buttons GTK_STOCK_CLOSE       			\
		-geometry "300x100"         			\
		-timeout "1"					\
		-fg "#255261"       				\
       		-bg "#C1B5B5"       				\
		"Proxy set"
	;;
103)	
	status=$(gconftool-2 -g /system/http_proxy/use_http_proxy)
	case $status in
		true)
			export export http_proxy=http://username:password@192.168.0.1:1234
		;;
		false)
			unset http_proxy
		;;
		*);;
		esac
	;;
*)
	status=$(gconftool-2 -g /system/http_proxy/use_http_proxy)
	case $status in
		true)
			export export http_proxy=http://username:password@192.168.0.1:1234
		;;
		false)
			unset http_proxy
		;;
		*);;
	esac				
	gmessage -title "Proxy Select"				\
		-buttons GTK_STOCK_CLOSE       			\
		-center 					\
		-geometry "300x100"         			\
		-timeout "1"					\
		-fg "#255261"       				\
       		-bg "#C1B5B5"       				\
		"No changes were made"
	;;
esac
```

This scrip also sets and unsets the gnome proxy settings. You need to seed these proxy settings directly in the gnome proxy tool (gnome-network-preferences) and this scrip simply switches that on or off.

WARNING: First time scriper at work, so this comes with zero guarantees. But it works like a charm for me :)

---

