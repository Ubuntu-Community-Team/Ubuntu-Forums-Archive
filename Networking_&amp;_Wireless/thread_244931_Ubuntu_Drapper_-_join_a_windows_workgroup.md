---
title: "Ubuntu Drapper - join a windows workgroup"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by kdog on 2006-08-27
Hi there,

can I join a Windows Workgroup whith Drapper?

If yes, how do I do that.

Thank`s in advance
Ken

---

### Post by Guy2 on 2006-08-27
I have the same need, and have some bizarre experiences to repoprt.

In the desktop menu, select Places > Network Servers (or somthing like that).
In the window that opens, click your way through and with luck you will see your windows workgroup in there somewhere. Click it to open it, and see which hosts it has picked up.

Now go back to the main menu and select Places > Connect to server.
Enter the hostname at the top and a name for the desktop icon at the bottom - I found that this had to be different from the server name or the whole thing crashed and burned. 

Anyway, using the above I got a nice icon on my desktop which I opened to launch a browser onto my Windows PC. Cool!

<power down. sleep overnight. power up>

Next time round, my workgroup was gone from Ubuntu and my nice icon led to an empty browser and pathetic error message.

All through, one thing has been consistent: the Network Admin tool has consistently refused to see my Windows PC - even when I was browsing it! (and since my router is acting as a DHCP server it is allocating IP addresses dynamically so I can't find out what to ping.)

Go figure.](*,) 
Better still, then come back and tell me how to get it back.

I'm beginning to feel that Ubuntu is a lot like Windows. It's dead simple to use - once you have been shown the crazy location for the tool, and the bizarre option to click on. Then it works if it feels like it - or not, as the case may be. Grr!

---

### Post by breuerp on 2006-08-27
> **kdog said:**
> Hi there,

can I join a Windows Workgroup whith Drapper?

If yes, how do I do that.

Thank`s in advance
Ken

First make sure you install samba:
sudo apt-get install samba

Next, I recommend you actually make your samba:
sudo gedit /etc/samba/smb.conf

Change the line that says "workgroup = XXXX" and replace it with the workgroup you're trying to join.

---

### Post by Guy2 on 2006-08-28
In my case (where my Windows workgroup came and went), I already have a /etc/samba directory. Can I take it that Samba is already installed?

My samba.conf file is blank. Nada.

Where do I go from here?

---

### Post by Guy2 on 2006-09-02
Just an update: all now working fine. I can happliy browse my Win PC's filesystem from Dapper.

It eventually fixed itself over a period of several days' random symptoms of one thing or another. One of life's little mysteries, I guess.

---

### Post by myname on 2006-09-06
I am having a similar behavior.  I recently installed Dapper Drake(and Samba), and tried to connect to my windows XP network at home, no dice.  I've been working on this problem for 3 days now.

I took the live CD into work, popped it in and booted it up to show my co-workers, went to Places -> Network Servers and browsed my companies Windows' workgroup and connected to the file server with no problem.

I brought the live Cd back home, booted up my linux box with the live CD and VIOLA, I can browse my Windows XP workgroup from the live CD.  I restarted, pulled the live CD out, and let the machine boot back to Dapper, and BZZZZZ, no dice on the browsing my windows workgroup.  I can see the servers, but when I click on the servers to connect to see what's shared, nothing.  Yet all works well from running the live CD.

Any ideas?

--Kevin

---

### Post by tbonius on 2006-09-06
That is a strange issue.  Maybe there is an SMB.conf difference between the two.  I recommend starting by making sure the Master Browser for the NetBIOS service is disabled.. heres a simplistic /etc/samba/smb.conf example file to start with.

Back up your old one and try something like this:

```
# Global parameters
[global]
        workgroup = WORKGROUP
        server string = Ubuntu
        security = SHARE
        preferred master = No
        local master = No
        domain master = No

[Share]
        path = /share
        read only = No
        guest ok = Yes

```

This is a basic example.

Restart Samba (sudo /etc/init.d/samba restart) and see if you can browse the share(s) on your Ubuntu computer.  Also try and see if you can use the Gnome SMB-ioslave frontend (I assume that is what you are using) to browse remote Windows SMB shares from your Ubuntu computer.

Also make sure your IP settings (including Netmask and gateway settings) are absolutely correct.  Also.. it helps to use DNS for name resolution in alot of cases as well.. but that is another topic for another time:

-Shameless Plug-

[http://www.section6.net/wiki/index.php/Main_Page]("http://www.section6.net/wiki/index.php/Main_Page")

Linux and BSD online tutorials

---

### Post by myname on 2006-09-06
Nope, didn't help.  :(

Let me re-explain.  

From Windows, I can see and browse my Ubuntu (Dapper Drake) shares

from Ubuntu, when I go into the network I can see the workgroup, and the servers within the workgroup, but when I click on a server to see the shares I get the popup box saying that they can't be viewed. 

I can see the shares if I ALT-F2 and then smb://192.168.0.2, but still can browse through Places/Network.

However, if I boot to the live CD, I CAN browse my workgroup/servers/shared folders through Places/Network.

i am in the process of reinstalling Ubuntu and starting from scratch...again.

--kp

---

### Post by myname on 2006-09-06
Update...

When I put in the live CD (dapper drake), to reinstall, I decided to test the browsing of the windows network again, and what the heck, I can no longer browse the windows network from Ubuntu.  

Nothing has changed on my windows box.  what the heck.

--kp

---

