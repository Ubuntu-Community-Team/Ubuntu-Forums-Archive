---
title: "Samba setup"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by DeMus on 2008-05-11
Hello,

I am relatively new to Linux although I managed to set up my computer with all the necessary Ubuntu software and settings.
What still doesn't work is Samba. I simply can not get a connection to my other (Windows) computers.
Since my printer is connected to the Linux machine I have to share it and need Samba.
Can somebody please give me a step by step tutorial on how to setup Samba?
Thanks very much.

DeMus

---

### Post by DeMus on 2008-05-11
So far I managed to have Samba installed and now I can see a shared folder on the Windows machine directly from Ubuntu.
What does not work is vice-versa: from the Windows machine I can not see the Ubuntu computer at all. It is as if the computer does not exist. I can ping the IP-address, but not the Ubuntu computer name. So I think DNS is not working.
How to move on from here?

DeMus

---

### Post by .rdg on 2008-05-11
You have to set up samba first. I don't know if there's a GUI for that (might be), because I'm used to manually changing the configuration file.

Take a look at /etc/samba/smb.conf which is responsible for setting up your samba server. As to computer name - I would recommend you using your IP when trying to reach Ubuntu server from Windows client (i.e. \\192.168.1.5).

---

### Post by Iowan on 2008-05-12
[This]("http://ubuntuforums.org/showthread.php?t=202605") is my favorite Samba How-To. Although there is a Samba configuration guide around here somewhere, I can't remember where.

---

### Post by DeMus on 2008-05-12
> **Iowan said:**
> [This]("http://ubuntuforums.org/showthread.php?t=202605") is my favorite Samba How-To. Although there is a Samba configuration guide around here somewhere, I can't remember where.

Thank you for your answer. Unfortunately it didn't work. There is something else wrong here. From my Windows computer I can not see the Linux computer at all. Not via computername, not via IP-address. It is as if the Linux machine is not there.
From the Linux machine I can get contact with the Windows machine, that's no problem. I can see folders, copy files, everything.

The question is now: how do i make the Linux machine visible on the network?

Any ideas?

Thanks,
DeMus

---

### Post by .rdg on 2008-05-13
Is your samba server working in the first place? Try doing the following (in terminal - it's easiest for me this way):

netstat -lt

There should be lines reading:

tcp 0 0 localhost:netbios-ssn *:* LISTEN
tcp 0 0 localhost:microsoft-ds *:* LISTEN

It would mean your samba is in fact working. Next, please post your /etc/samba/smb.conf so we can help you out.

Additionally check whether there's something added in your /etc/hosts.deny - TCP Wrapper might be also blocking (but that's higly unlikely).

---

### Post by DeMus on 2008-05-13
Hi,

Thanks for your answer. This is what happens when I type the netstat command:

jan@2-Quad:~$ netstat -lt
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     
tcp        0      0 *:ipp                   *:*                     LISTEN     
tcp        0      0 localhost:31416         *:*                     LISTEN     
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     
tcp6       0      0 [::]:ipp                [::]:*                  LISTEN     

I uploaded my smb.conf file smb.conf.txt because of file limitations here. I hope it help you, cause it didn't help me.

DeMus

---

### Post by Iowan on 2008-05-13
Might try```
 ps aux |grep mbd

```to see if smbd and/or nmbd are running.  Also, how does your machine get IP address - static or DHCP? If DHCP, there's an option in **/etc/dhcp3/dhclient.conf** to "send hostname=".

---

### Post by DeMus on 2008-05-13
My Linux box has a static IP address, so no DHCP necessary.

Your command replied this:

jan@2-Quad:/etc/dhcp3$ ps aux |grep mbd
root     17639  0.0  0.0  75276  2444 ?        Ss   May13   0:00 /usr/sbin/smbd -D
root     17643  0.0  0.0  75276  1008 ?        S    May13   0:00 /usr/sbin/smbd -D
jan      26906  0.0  0.0   5160   840 pts/0    R+   03:34   0:00 grep mbd

Thanks for all your help. I really appreciate it.

DeMus

---

### Post by .rdg on 2008-05-14
Your smb.conf file is written wrong. Lines that definitely is wrong is:

interfaces = 127.0.0.1/8 192.168.0.0/24

While it should be something like:

interfaces = lo eth0

Then you should consider writing the following network addresses in:

hosts allow = 127.0.0.1/8 192.168.0.0/24

Please post your network card configuration, so I can double check that your IP address matches the addresses given in the above 'hosts allow' line.

Regards.

---

### Post by DeMus on 2008-05-14
Hi again,

I did not change anything to my smb.conf file, so it must have been set to this by using the installation program and/or changing settings in the setup.

You asked for my networkcard configuration. I got the info in 2 .png files. I hope this makes things more clear for you.

DeMus

---

### Post by Iowan on 2008-05-14
Your smb.conf file looks WAAAY different than the one that came with my (Gutsy) installation - and no comments (SWAT?).

---

### Post by .rdg on 2008-05-14
Yes, these images (first one tbh) is just fine. So please edit your /etc/samba/smb.conf file with any text editor (Gnome's gedit is ok). Just run:

sudo gedit /etc/samba/smb.conf

Edit your configuration so you have:

interfaces lo eth0

hosts allow = 127.0.0.1/8 192.168.1.0/24

That should do it. There were 2 things wrong. Both of these were wrong in your case - interfaces should list your network cards, not network addresses. Second - hosts allow was not allowing your network (I guess your other pc/pcs in LAN have IPs like 192.168.1.x, not 192.168.0.x). Check back here after you made the changes I mention above. Also - if it doesn't work you can delete the line with hosts allow, so you allow anyone to connect to your PC (after authenticating).

Hope this solves the case.

---

### Post by DeMus on 2008-05-14
You are good. I still have no idea how the wrong info got into the conf file but I sure am happy it is solved now.
When I want to connect a third PC, also Windows OS, I have to change nothing, haven't I, since also this one is in the same ip-address range and on the same workgroup.
Thank you so much for all your help, I will try to remember the solution incase I need it again someday.
Just a question, where are you from? I live in The Netherlands in a small town called Hardenberg on the east border with Germany.

DeMus

---

### Post by Iowan on 2008-05-14
> **DeMus said:**
> When I want to connect a third PC, also Windows OS, I have to change nothing, haven't I, since also this one is in the same ip-address range and on the same workgroup.
Third PC in same workgroup and subnet *should* work.

---

### Post by .rdg on 2008-05-14
As for the third and any other PC - as long as it's on the same subnet it's allowed to connect after successful authorization.

As to my location - I live in Poland, Jaworzno (already a city, but not a big one). Glad I could help, enjoy your Ubuntu BLING :-)

---

