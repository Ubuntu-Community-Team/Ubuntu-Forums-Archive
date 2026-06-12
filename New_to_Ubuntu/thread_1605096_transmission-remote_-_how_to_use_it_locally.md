---
title: "transmission-remote - how to use it locally?"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by Abdus on 2010-10-24
I just reinstalled Ubuntu. Before reinstall I **locally** used transmission-remote and its fabulous ultra simple web interface. I don't remember how I set it up then and I can't find a solution in the web. 

I used to access my downloads just by visiting
[http://localhost:9091/transmission/web](http://localhost:9091/transmission/web)
but now this address gives me error: "Could not connect to remote server" (full text at the end of this post).

Intuition tells me I'll have to install a www server... but then the other intuition replies that there has to be a simpler solution. :)

```
Could not connect to remote server
You tried to access the address [http://localhost:9091/transmission/web](http://localhost:9091/transmission/web), which is currently unavailable. Please make sure that the web address (URL) is correctly spelled and punctuated, then try reloading the page.
Make sure your Internet connection is active and check whether other applications that rely on the same connection are working.
Check that the setup of any Internet security software is correct and does not interfere with ordinary web browsing.
If you are behind a firewall on a Local Area Network and think this may be causing problems, talk to your systems administrator.
Try pressing the F12 key on your keyboard and disabling proxy servers, unless you know that you are required to use a proxy to connect to the Internet. Reload the page.
Need help?
Open the Opera Help.
Go to Opera's online support desk.
```

---

### Post by jtarin on 2010-10-24
[Could this help?]("https://trac.transmissionbt.com/wiki/WebInterface")

[And here.]("http://www.webupd8.org/2009/12/setting-up-transmission-remote-gui-in.html")

---

### Post by Abdus on 2010-10-24
> **jtarin said:**
> [Could this help?]("https://trac.transmissionbt.com/wiki/WebInterface")

Didn't help.

> **jtarin said:**
> [And here.]("http://www.webupd8.org/2009/12/setting-up-transmission-remote-gui-in.html")

As above. I visited this link before (Google is my friend too), but although very informative, it doesn't deal with my problem.

Either 
[http://localhost:9091/](http://localhost:9091/)
or
[http://127.0.0.1:9091/](http://127.0.0.1:9091/)
just give me "Could not connect to remote server".


PS. As I was writing this very post, it came to my head - unlock the port. Will try and report. :D

---

### Post by jtarin on 2010-10-24
The first link has links to documentation on setting up your config files for remote host, I assume you have read those too?

---

### Post by papibe on 2010-10-24
I just want to check if you know how transmission-* works. The process doing all the work is called transmission-daemon, and when you go to [http://localhost:9091](http://localhost:9091) it's a way to both, get info and to pass commands to the daemon. Both command line clients, transmissioncli and transmission-remote, work in a similar way.

First of make sure transmission-daemon is installed and running:
```
$ sudo service transmission-daemon start
```
As a double check you can do:
```
$ ps aux | grep transmission-daemon
```
In order to see if transmission-daemon is receiving commands, you can check for the list of torrents:
```
$ transmission-remote -n transmission:transmission -l
```

After you check that, try to connect again to the web interface.

Good Luck.

---

### Post by Abdus on 2010-10-24
> **papibe said:**
> First of make sure transmission-daemon is installed and running:
```
$ sudo service transmission-daemon start
```

That's it. :) Daemon wasn't running. As soon as I started it, I stopped to get the "couldn't connect" error. Thank you. 

Now, however, I can't display the page because it wants a username and password. I tried to change those, but then it still doesn't let me pass through the log in pop-up:
```
transmission-daemon -u MyName -v MyPass
```

I bet it's something trivial again. :)


EDIT:
Hmm, another error:
```
abd@ubayd:~$ transmission-remote MyName:MyPass -n transmission:transmission -l
[04:53:47.541] transmission-remote: (http://abd:0/transmission/rpc) Couldn't resolve host name

```
Seems that command line wise the username and password work - they don't in the browser though. Or it's the error that prevents the browser from showing me the contents of the page. I'm lost. It wasn't so complicated when I did it the first time. :D

EDIT2:
Got it working. How - don't ask me. First changed the username and password using the GUI Preferences. It still didn't work. Then I changed them again in command line. Voila - all available. Linux Magic + User Newbieness = Miracles.

Thank you for help.

---

### Post by papibe on 2010-10-24
Default username: transmission
Default password: transmission

In order to change any of those, you need to take another direction. First, stop transmission-daemon:
```
$ sudo service transmission-daemon stop
```
Then you'll need to edit the config file. As a safety measure backup the file first.
```
$ sudo cp /etc/transmission-daemon/settings.json  /etc/transmission-daemon/settings.json.backup. If you know how to use vi, edit it like this. If not change vi for nano.
$ sudo vi /etc/transmission-daemon/settings.json
```
The key lines are:
```
"rpc-username": "transmission",
"rpc-password": "{98f4.....",
```
Change them to your needs, for example:
```
"rpc-username": "NewUser",
"rpc-password": "NewPassword",
```

Save the file and restart transmission:
```
$ sudo service transmission-daemon start
```
Now you can use transmission-remote with the new values:
```
$ transmission-remote -n NewUser:NewPassword -l
```

Regards.

BTW: your password, will be "encrypted" (change to a format "{9809..."), next time daemon is stoped.

---

### Post by jtarin on 2010-10-25
> **Abdus said:**
> Didn't help.



As above. I visited this link before (Google is my friend too), but although very informative, it doesn't deal with my problem.

Either 
[http://localhost:9091/](http://localhost:9091/)
or
[http://127.0.0.1:9091/](http://127.0.0.1:9091/)
just give me "Could not connect to remote server".


PS. As I was writing this very post, it came to my head - unlock the port. Will try and report. :D


From the link I gave you:

```
Configure transmission-daemon



_**If you are reading**_ this how-to, you must be wanting to run transmission-daemon remotely.
```

---

### Post by Abdus on 2010-10-25
I run into another problem: can't change the download directory. When I edit the settings file
[FONT="Courier New"]sudo vim /etc/transmission-daemon/settings.json[/FONT]
the only line about that is:
[FONT="Courier New"]"download-dir": "/var/lib/transmission-daemon/downloads",[/FONT]
(which seems to be a file)
however the actual download path is
[FONT="Courier New"]/home/myname/Downloads[/FONT]

Any tips?

I tried to change it in Transmission GUI - however despite it being changed the new torrents are downloaded to the wrong (default) path.

---

### Post by papibe on 2010-10-25
As I understand, the GUI side of transmission (transmission-gtk and transmission-qt) works as whole application, and independently of the others (remote, cli and daemon).

So to change the download directory for daemon/remote you need to stop the daemon, edit the file and start it again. Note that torrents that are already started will continue to be downloaded in the directory they started. The new ones will go to the one you setup.

Regards.

---

### Post by jtarin on 2010-10-25
As papibe states and from the documentation it specifically states that anytime you edit any parameters of the non-gui applications you must stop the daemon or the changes will have no effect.

---

### Post by Abdus on 2011-05-01
@jtarin & papibe: Thank you both for your help from before a few months. :)

Got a new question regarding transmission-remote: Surprisingly no torrents are being leeched right now, even though some are being seeded. I suppose this might have something to do with a machine reboot that was stopped (in panic) before it was executed, and some ports might have been closed or… something like that.

I tried:
$transmission-remote -n transmission:transmission -pt
it says:
Port is open: No

What do I do now? :-k

---

### Post by papibe on 2011-05-01
Are you using a firewall in the machine transmission-daemon is running? if so, you need to open the port on your machine.

Then you need go to your router and open and forward it to the machine.

If you haven't change it, it should be port 51413. In the case you change it, remember that it is the one with the field  "peer-port" in your file:
```
/var/lib/transmission-daemon/info/settings.json
```
If you need details on how to open and forward the port on your router, check this site: [PortForward.com]("http://portforward.com/routers.htm").

I hope it helps.

---

### Post by Abdus on 2011-05-01
False alarm - I switched on some totally random torrents with massive numbers of seeders and some of them kicked in. Thus I know the problem is NOT on my side, just my torrents are somehow broken.

Funny thing is that -pt still shows:
Port is open: No

I wouldn't have a slightest idea how to do what you told me. :)

Thank you for your help.

---

