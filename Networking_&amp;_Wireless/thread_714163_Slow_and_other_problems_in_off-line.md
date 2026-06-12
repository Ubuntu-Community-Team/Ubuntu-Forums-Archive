---
title: "Slow and other problems in off-line"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by Chainz on 2008-03-03
Hi, 
I noticed this problem accidentally when my network went down.
When my computer is off-line it takes long seconds to start simple programs like Terminal or Text Editor, up to 10-20 seconds. :confused:
Even MySQL is not starting, I get: "Can't connect to database" error. (Apache works fine, though).
Same happens on my both machines :(

Why when network is up, all works fine?


Same was reported here: [http://ubuntuforums.org/showthread.php?t=620093]("http://ubuntuforums.org/showthread.php?t=620093")


I hope you can imagine how frustrating it can be when you're using laptop that sometimes can't be connected.

---

### Post by unutbu on 2008-03-03
Chainz, this is not a wholly satisfactory solution, but if you type
```

sudo ifdown <interface>

```

where <interface> is eth0 or wlan0 or whatever,then the apps will no longer be slow to start. The problem is, you'll need to wait to open up a terminal to enter the command. 

Congratulations, you have reached the end of my knowledge. What follows is speculation,  so please take it with a spoonful of salt:

1) You might try adding a menu item with Preferences>Main Menu with the above line as the command. That way you might be able to execute the command without needing to open a terminal.

B) You might want to edit the "timeout" line in /etc/dhcp3/dhclient.conf. 
From 
```
man dhclient.conf
```

"The timeout statement determines the amount of time that must pass  between  the
time that the client begins to try to determine its address and the time that it
decides that it’s not going to be able to contact a server."

Make it shorter, and perhaps you won't have to wait as long.

III) edit /etc/network/interfaces: Change

auto wlan0

to

#auto wlan0

(Change wlan0 to whatever your interface is). This will stop your machine from trying to bring up this interface at boot time. (man interfaces for details). You can then manually start the interface only when you want it by typing

```
sudo ifup wlan0
```

iv) If you are serious about solving this problem, a real solution would be have some kind of "boot profile" setup so that at boot time you could press a key to define if you want a networked session or a non-networked session. I know nothing about how to do this. Perhaps google words like "ubuntu laptop network boot profile". Maybe try
[http://hprofile.sourceforge.net/faq.php](http://hprofile.sourceforge.net/faq.php) or
[http://ubuntuforums.org/showthread.php?t=296808](http://ubuntuforums.org/showthread.php?t=296808)

If you find something simpler, please post your solution.

---

### Post by Chainz on 2008-03-04
Will try that for sure...

However why programs that should not relay on internet, like Text Editor, check weather it's up or not?
Why MySQL is not starting at all???

Sorry, but I just believe it's a horrible bug, isn't it? :(

---

