---
title: "Connot see Windows computers"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by Florida Cracker on 2008-06-30
I have been leaning Ubuntu for a couple months now and have managed to setup samba to where I can access Ubuntu computer from windows machines but I am unable to view the windows machines from Ubuntu. I have read that it is supposed to do this "out of the box". I can see the Home network in Windows Networks and at times see icons for the other machines, but I am unable to view their shares. This is with computers running XP, 98, and Vista. Any advise?

---

### Post by superprash2003 on 2008-06-30
go to the terminal(applications->accessories->terminal) and type sudo nautilus smb://x.x.x.x  and replace x.x.x.x with the ip address of the xp pc

---

### Post by Florida Cracker on 2008-06-30
I'll give that a try, although; how about the computers running win98? And what about the dynamic IP issue? Will I have to assign each computer with a static IP and do this for all of them? The router I have currently assigns the IP's.

---

### Post by Sudan on 2008-07-03
> **superprash2003 said:**
> go to the terminal(applications->accessories->terminal) and type sudo nautilus smb://x.x.x.x  and replace x.x.x.x with the ip address of the xp pc

How do I find the IP address of my xp machine?  I'm having a similar problem.

---

### Post by lisati on 2008-07-03
> **Sudan said:**
> How do I find the IP address of my xp machine?  I'm having a similar problem.
On a Windows machine, you can run ```
ipconfig
``` from the command line, and it will tell you the ip address(es) currently assigned to your machine.

EDIT: this works on win 98SE & XP home, I don't know about Vista since I haven't used it.......

---

### Post by Sudan on 2008-07-03
> **lisati said:**
> On a Windows machine, you can run ```
ipconfig
``` from the command line, and it will tell you the ip address(es) currently assigned to your machine.

EDIT: this works on win 98SE & XP home, I don't know about Vista since I haven't used it.......

Thanks, got the IP.  I ran the terminal sudo nautilus command go this error:

kelvin@NeoV:~$ sudo nautilus smb://192.168.2.2
seahorse nautilus module initialized
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:7067): WARNING **: Unable to add monitor: Operation not supported
                                                   
kelvin@NeoV:~$ 

Help please? Thanks.

---

### Post by needarealname on 2008-07-04
I received the same message as Sudan did.  Any ideas?

---

### Post by slavka012 on 2008-07-04
Me too...

---

### Post by Florida Cracker on 2009-02-18
I finally solved my problem.
I did a sudo gedit on my nsswitch.conf file and added wins in front of dns in the hosts:files line. Now all windows shares show up and are easily accessed. Hope this helps others with same problem.

---

### Post by sbrandon on 2009-02-18
Florida = could you give the entire sudo line to modify the nsswitch.conf file. I just go to a blank file.

---

### Post by Florida Cracker on 2009-02-18
sudo gedit /etc/nsswitch.conf
then scroll down to hosts:files and put wins ahead of dns on that line. (************ wins dns *****)
If this doesn't work for you, go to hosts tab in networking and add the IP number and the computer name(in aliases). I already had them set up so I don't know if it is required. (hopefully not if you have dhcp) I will see if it works with a computer thats not already set up by ip in the hosts list tonight if I get a chance.

---

### Post by Florida Cracker on 2009-02-19
You will have to add the IP address into the hosts tab in order to access the windows computer. I removed the address of an XP computer that was working and after restarting the ubuntu box it was no longer accessable. After adding it back in and restarting, it worked again. I believe it is located in system, administration, network and under the hosts tab. Add the IP address and name (alias) of the windows computer and restart. If you have DHCP you will have to do this again when it reassignes it another IP address. When I get some extra time on my hands I will start reconfiguring my home network to static IP's.

---

### Post by ajkenney on 2009-02-19
I've got the same problem except that even the Windows boxes can't see my Ubuntu box on the network.  I've tried to configure SAMBA (using the GUI frontend).  I change the numerous settings to what I think they should be (not having any guide to go by) but, still no go.  The Windows boxes can't see me and I can't see them.

After reading the above posts, it dawns on me that there should be some type of setting that will account for DHCP changes of the IP address of the various boxes on the system.  Would this setting just use the name of the box instead of the IP address?

Is there anyone out there that has successfully set up a home network (or absolutely knows how) that can tell us exactly where to get this information from and/or give some examples of config files.

For anyone who wants to help, I have six computers on my home network (not counting the XBOX360).  One each for my two sons, one for my daughter, one for my wife, one entertainment system, and my lone linux box.  5 Windows boxes and one Ubuntu box.  I'd just like to have file and printer sharing with the Windows boxes, nothing more exotic than that.

Cheers,

Andy

---

### Post by Florida Cracker on 2009-02-19
Setting up smb.conf file was the easy part. Getting ubuntu to access the windows boxes took me a lot of research which I feel it should not have required. Read this link... [http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/](http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/)

There is also a nice youtube video on how to do this... well there was one on there a year ago anyway.
You will also need to set the folder properties to share after you modify the smb.conf file.

---

### Post by Florida Cracker on 2009-02-19
The video is still there.
[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

---

