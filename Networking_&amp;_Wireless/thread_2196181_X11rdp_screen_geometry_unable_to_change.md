---
title: "X11rdp screen geometry unable to change"
date: 2013-12-28
forum: Networking &amp; Wireless
---

### Post by rounaksingh17 on 2013-12-28
[FONT=arial]hi guys,
[/FONT][FONT=arial]I am working with the Remote Desktop. So, I have install xrdp and its working fine. Though I am unable to change the screen geometry of the remote client as there is just one resolution option(1024x768) in the display properties.

xrdp  is running on Ubuntu12.04.

I have checked the log xrdp-sesman.log 

```
[20131228-17:35:20] [INFO ] A connection received from: 127.0.0.1 port 34262
[20131228-17:35:21] [INFO ] scp thread on sck 8 started successfully
[20131228-17:35:21] [INFO ] ++ created session (access granted): username remote, ip [192.168.21.106:4534]("http://192.168.21.106:4534/") - socket: 8
[20131228-17:35:21] [INFO ] starting X11rdp session...
[20131228-17:35:21] [INFO ] An established connection closed to endpoint: NULL:NULL - socket: 9
[20131228-17:35:21] [INFO ] An established connection closed to endpoint: NULL:NULL - socket: 9
[20131228-17:35:21] [INFO ] An established connection closed to endpoint: NULL:NULL - socket: 9
[20131228-17:35:21] [INFO ] An established connection closed to endpoint:[127.0.0.1:34262]("http://127.0.0.1:34262/") - socket: 8
[20131228-17:35:21] [INFO ] An established connection closed to endpoint: NULL:NULL - socket: 7
[20131228-17:35:21] [INFO ] An established connection closed to endpoint:[127.0.0.1:34262]("http://127.0.0.1:34262/") - socket: 8
>>>>Problem>>>>[20131228-17:35:21] [INFO ] X11rdp start:X11rdp :10 -geometry 1024x768 -depth 24 -bs -ac -nolisten tcp -uds
[20131228-17:35:21] [INFO ] starting xrdp-sessvc - xpid=4130 - wmpid=4129

```

I have tried changing the params of sesman.ini and put 

```

[X11rdp]
param1=-bs
param2=-ac
param3=-nolisten
param4=tcp
param5=-uds
param6=-geometry
param7=1600x900

```

But resolution is not changing. [/FONT]:([FONT=arial]
In addition, the execution of X11rdp in logs (xrdp-sesman.log) becomes like this

 ```

X11rdp start:X11rdp :10 -geometry 1024x768 -depth 24 -bs -ac -nolisten tcp -uds -geometry 1600x900

```

and X11rdp is taking first resolution or geometry (ie 1024x768)

There is no good documentation here and there I have checked all.
After wasting a day of this problem I think what I need is the following in the initializing script

```

 X11rdp start:X11rdp :10 -geometry 1600x900 -depth 24 -bs -ac -nolisten tcp -uds

```

But I think the xrdp is taking 1024x768 as default.
[/FONT][FONT=arial]
Please help.[/FONT][FONT=arial]
[/FONT]
[FONT=arial]Thanks[/FONT]

---

### Post by rounaksingh17 on 2014-01-01
I have a reply :):) from Laxmikant Rashinkar through xrdp mailing-list. He wrote me that the screen geometry must be set from the client side. For example if using rdesktop or FreeRDP as client         use the option -g 1920x1080. If using mstc, use the GUI         to configure the new geometry. So, in this way the client need to send the geometry and color depth.

Now, I have changed the screen geometry. My problem is solved:o:o, so closing the thread.

---

