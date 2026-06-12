---
title: "Grsync can't see network"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by edzell on 2010-08-12
I want to use grsync to sync between my networked laptop & desktop machines. I'm trying to do it from laptop to desktop, but the destination dropdown doesn't show the network; even though the remote desktop (home) folder is shared and mounted. Is this a deficiency in the GUI or am I missing something?

I guess I could enter the destination path manually but haven't so far come up with anything the program will accept. Anyway I want to get the GUI to work properly if possible.

---

### Post by ubunterooster on 2010-08-12
Try doing it manually to see if that works; troubleshooting

---

### Post by edzell on 2010-08-12
> **ubunterooster said:**
> Try doing it manually to see if that works; troubleshooting

I've tried that but don't know exactly how to address the remote computer; by name followed by a colon followed by a space or ? ..... and is the name case sensitive? In some places it shows up in capitals, in others with only the first letter capitalised (probably the way I originally typed it.)

I haven't yet created a destination path that grsync will recognise.

---

### Post by Jeff_Illingworth on 2010-09-02
I'm also interested in this topic. I haven't been able to use grsync to backup across a network. Is this an issue with rsync or a problem with the gui?

---

### Post by mapes12 on 2010-09-02
Hi Guys

Can you see your target machines. Go Places>Network and have a look.

Have you shared the source?

If for whatever reason sharing isn't working then try to connect the UBU boxes with SSH. Post back for a HowTo if required.

---

### Post by edzell on 2010-09-04
Thanks for the response.

In my case both machines can see each other and each other's shared  /home folder. But the browse boxes in grsync's GUI see only their own host  computer - no network. Is rsync, and/or grsync, only meant for synchronising within a  single machine? Seems unlikely: Maybe it's a GUI bug or omission.

Don't know beans (coffee or otherwise) about SSH so please feel free to instruct. I'm a bit long in the tooth & not very Linux (or???) savvy. Almost exclusively a GUI_GUY.

Edited to add: 
- Is grsync "stand alone" or should I have rsync installed first? 
- I found a post about manually editing rsyncd.conf to define allowable hosts & servers:
  1) Do I have to do this?
  2) I can't find the file in /etc where it's apparently supposed to be.

Edzell.

> **mapes12 said:**
> Hi Guys
Can you see your target machines. Go Places>Network and have a look.
Have you shared the source?

If for whatever reason sharing isn't working then try to connect the UBU boxes with SSH. Post back for a HowTo if required.

---

### Post by Jeff_Illingworth on 2010-09-08
Guys,

     I don't know if this'll help, but I found this HowTo helpfu  :[http://ubuntuforums.org/showthread.php?t=795668&highlight=grsync+network](http://ubuntuforums.org/showthread.php?t=795668&highlight=grsync+network)

---

### Post by mapes12 on 2010-09-08
**Here's my HowTo to get SSH up and running on your Ubu boxes:-**

It goes like this for me:

I guess what you want is file sharing between two linux boxes - there is NO WINDOWS involved.

1.) Make sure the openssh-server and openssh-client are installed on both machines.

```
sudo apt-get install ssh
```Is a meta package and will install both applications. Or you can search for it in Synpatic and install it from there.

2.) Go to the machine you want to connect to. You need to find the machines IP address. You can do this by either of the following ways:-

1. GUI - Right click Network Manager icon. Select "Connection Information". Note down the **IP Address**.

2. In Terminal:

```
ifconfig
```

This should give you an output just like this one

> eth0 Link encap:Ethernet HWaddr 00:50:da:e0:67:74
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:9 Base address:0xc000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:27 errors:0 dropped:0 overruns:0 frame:0
TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1732 (1.7 KB) TX bytes:1732 (1.7 KB)

wlan0 Link encap:Ethernet HWaddr 00:11:50:dd:a9:16
inet addr:**192.168.1.68** Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::211:50ff:fedd:a916/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1769 errors:0 dropped:0 overruns:0 frame:0
TX packets:1639 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1661090 (1.6 MB) TX bytes:342426 (342.4 KB)

wmaster0 Link encap:UNSPEC HWaddr 00-11-50-DD-A9-16-39-31-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Your output can differ quite a bit, but the important information is just the bold bit. These four numbers are the address of the machine (do not use the 127.0.0.1 address - this the internal address of your network adapter).

So, in my case the address would be 192.168.1.68

3.) Access the computer
Now, when you want to access a computer from the other, go to places>connect to server.
- Choose SSH as the "service type" from the drop down list
- the server is the IP of the other computer (the one you want to access)
- the port can be left blank (this means it assumes port 22)
- the folder you should put in is /home - but you can leave it blank in which case you will access the other machine at "/" level and then navigate to /home/username
- the username *must* be specified. This is the user you use to log into the other computer.
- also, enable the bookmark and choose a name for it. This means this connection will always reappear in your places menu and in the sidebar(left) in your filebrowser

Click OK

You may get a message about keys on first time connection. Just OK it

You will then be asked for the password of the user of the other machine. Put it in, and if you do not want to be bothered by this anymore - choose always remember.

Now a folder should open with the folder on the other machine.

From this folder you will be able to browse the other machine and transfer files back and forth, including using the Grsync browse function.

Hope this helps.

Mark

:p

---

### Post by edzell on 2010-09-08
Thanks Jeff & Mapes for the URL & detailed response. I've got other things on my plate right now but will follow the instructions in due course.

Meantime, in anticipation, I'll mark my problem solved.

EDIT: Taking that back because I should have mentioned there will be a third, Windows, machine involved. I now realise SSH isn't supposed to work with Windows so for me it's not a solution. But I guess the thread will suffice for whoever is OK using SSH, so on their behalf I'll leave it as solved & persevere with Samba as discussed here:

[http://reformedmusings.wordpress.com/2010/05/22/samba-file-sharing-in-ubuntu-lucid-10-04-lts/](http://reformedmusings.wordpress.com/2010/05/22/samba-file-sharing-in-ubuntu-lucid-10-04-lts/)

Damn, why can't I ever discover where to do mark Solved. :confused: 

Edit: Oh now I get it - you have to go to the top of the thread.

---

