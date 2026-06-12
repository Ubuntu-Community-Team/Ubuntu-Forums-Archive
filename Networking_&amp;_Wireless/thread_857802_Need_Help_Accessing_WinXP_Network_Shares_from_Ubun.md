---
title: "Need Help Accessing WinXP Network Shares from Ubuntu"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by Psipherious on 2008-07-12
I've just installed Ubuntu (8.04 i386) the other day and have just finished getting most things working, the only thing I'm really having trouble with still is the networking.

I don't need to access the Ubuntu folders from other machines only need to access the shared folders on my other Windows XP machines. As far as I can tell Ubuntu is just supposed to be able to do this 'out of the box'.

I've read a number of threads but have yet to come across an answer to my problem. I also tried following the tutorial here: [http://www.europe.eclipse.co.uk/Ubuntu/804%20on%20Win%20Network.htm](http://www.europe.eclipse.co.uk/Ubuntu/804%20on%20Win%20Network.htm) up to the Step 1 part. The remaining steps I shouldn't need since I'm not trying to go the reverse way (not trying to access Ubuntu from the windows machines).

In the "Step 1" in that tutorial link above I get to the part where I double click on Windows Network, then enter my workgroup and I do indeed see all the computers on my network - I have 5 Windows XP systems hooked up on the network but then when I double click and enter on any of those machines, I can not see any of the shared folders whatsoever, I get no prompt asking me for the password to access the machine, etc.

All the WinXP machines are running Win XP Pro with SP2 and on a couple of the machines I have created some test directories and given them full access to "Everyone" and I've even created a user account on one of the machines with exact matching (including case) username and password as my Ubuntu account and applied it to my test folders.

I even *completely* uninstalled my firewall and disabled the Windows firewall on one of the machines to see if it was that, all of this to no avail.

I am still unable to even see a single shared folder on any of my WinXP machines let alone being able to double click on any of them to get a password prompt.

I get no password prompts just by entering the machine and I just see nothing inside each machine.

In actual Ubuntu the only settings I've really tried messing with are I edited my smb.conf so that the workgroup name is identical to the workgroup name of all the other computers on my network.

So my trouble is... why am I not able to see any of my shared folders at all - and how can I make it so that I am able to see them?

---

### Post by superprash2003 on 2008-07-12
firstly ensure that the ubuntu can ping the xp machines.. then go to the terminal and type sudo nautilus smb://x.x.x.x where x.x.x.x is the ip of the xp machine

---

### Post by Psipherious on 2008-07-13
I am able to ping the machine but when I try the sudo nautilus command, nautilus opens up at /root and gives the error window message: Couldn't display "smb://192.168.0.20" - Nautilus cannot handle smb: locations.

Yet, when I don't use a sudo command and I just run nautilus and browse to the network as mentioned above, the location listed in the location bar is smb://winxp-01

It just displays none of the folders that I have shared in that location.

None of the Windows XP machines have any trouble accessing the shared folders amongst each other.

I'm also typing this post from the Ubuntu machine which is connected to the Internet (and working fine online) through the same router that the rest of the machines are connected though.

---

### Post by Horomancer on 2008-07-14
Bump for related interested!
I'm very new to ubuntu but when i set up my machine a few month's back i did manage to gain access to my laptop running Vista and upload all my backuped files onto my Ubuntu box (was running 7.10 then)
I did this back then by going to System> Administration> Networking tools
at the top of the window is a box labled Network Device: which by default was set to Loopback interface (lo)
I found by selecting the drop back and changing to Ethernet Interface (eth0) i could gain access to my laptop. I have no understanding to why that worked or why Ubuntu was set to loopback as default. Since upgrading to Hardy, this doesn't seem to work. If i try to select eth0 and click on 'configure' i get an error message stating "The Interface does not exist. Check that it is correctly typed and that it is correctly supported by your system."

---

### Post by dmizer on 2008-07-14
for connecting to windows shares from ubuntu, please see the second link in my sig.

---

### Post by Psipherious on 2008-07-16
While this doesn't seem to allow me to display my shares by browsing though the network, it does allow me to mount the shared folders / drives and therefore allows access to them which is ultimately what I need for my own network so thanks, appreciate [that link]("http://ubuntuforums.org/showthread.php?t=288534").

It would still be nice to be able to browse the shares remotely without having to know exactly what they are though, in case either you don't recall all the shares that you want to access or you don't have direct access to the machine you want to read shared folders from. So I'm still wondering why it doesn't work the way it does in the tutorial I linked above where it displays the shares and then asks you for the password once you try to access that share. If anyone has any further information on why this would be? Is it a bug with 8.04.1 or something perhaps?

But thank you again as I am able to access my shares now since I do know the names of them all.

---

### Post by dmizer on 2008-07-17
my method uses the winbind daemon in order to provide name resolution and allows cifs to connect to the share correctly.

this is a trade off because winbind interferes with nautilus's ability to browse the windows network. so by connecting to the share with my method, you effectively disable nautilus ability to browse the windows network.

if you just want to browse the network (you will still be unable to connect to shares), you can temporarily disable winbind with the following command:
```
sudo /etc/init.d/winbind stop
```
when you're done browsing, you can restart it with this command:
```
sudo /etc/init.d/winbind start
```

---

