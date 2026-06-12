---
title: "[SOLVED] I can no longer see my Windows workgroup"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by boriquajake on 2008-01-03
When I first installed Ubuntu on a laptop I use mainly in my office I was instantly able to see the other computers in the office network and share the printers. It was like I had died and gone to OS heaven it was so painless. Anyway, I went on vacation for a week or two and now I can't see the other computers or their printers. How do I get back to nirvana?

We have a very basic small office setup. Three XP PCs and one Vista. They all are all connected by ethernet cables to the same MicroteK router. Everyone's internet access works and everyone else can see and share the printers that are connected to one of the XP PCs by USB cable. I am the one that plugged everything together originally and,  ignorant as I am, I am the designated tech so nobody has changed anything as far as I can tell.

If this should be in the absolute beginners forum please let me know.

---

### Post by disturbed1 on 2008-01-03
I hate this short coming of Windows Networking. Happens to me all the time with Windows to Windows, and Linux to Windows. Funny how Windows PCs never have an issue seeing my SMB Linux shares :roll:

In Nautilus hit ctrl L to go to the location entry field. Then type -

smb://Workgroup

Where Workgroup is the name of the Windows workgroup. You can also type in -

smb://192.168.1.144/C$

C$ being the share name
or

smb://Jewels/C$


Jewels being the name of the PC.

---

### Post by boriquajake on 2008-01-03
> **disturbed1 said:**
> I hate this short coming of Windows Networking. Happens to me all the time with Windows to Windows, and Linux to Windows. Funny how Windows PCs never have an issue seeing my SMB Linux shares :roll:

In Nautilus hit ctrl L to go to the location entry field. Then type -

smb://Workgroup

Where Workgroup is the name of the Windows workgroup. You can also type in -

smb://192.168.1.144/C$

C$ being the share name
or

smb://Jewels/C$


Jewels being the name of the PC.

What is "Nautilus"?

---

### Post by ARhere on 2008-01-03
Nautilus is the Ubuntu File browser/manager just like Explorer is the WindowsXP file browser/manager.  "My places, middle menu item.  Its what you open up to view files with"

-AR

---

### Post by dannyboy79 on 2008-01-03
what does smbtree without a passsowrd show? it will show you all computers and shares available to guests? can you issue 

smbclient -L computernamehere

you should enter the password for that computer and you should see all the shares available to that user and password.

have you tried restarting samba? maybe your nmbd damon isn't running so it's not connecting the master workgroup server?

ps aux | grep nmbd

---

### Post by boriquajake on 2008-01-03
Dannyboy,

I don't understand anything that you said. In fact I don't understand anything that anyone has said. I don't know how to open Nautilus and I don't know where to type in the things that people have suggested. 

I feel like an idiot.

---

### Post by SteveHillier on 2008-01-03
> **disturbed1 said:**
> 

In Nautilus hit ctrl L to go to the location entry field. Then type -

smb://Workgroup

Where Workgroup is the name of the Windows workgroup. You can also type in -

smb://192.168.1.144/C$

C$ being the share name
or

smb://Jewels/C$


I will try to translate.  
On the menu bar click 'Places' and then 'Computer'.
You are now in Nautilus.

In the location bar type in smb://<thenameofyourworkgruphere>

My workgroup is hillierconsult so I type in smb://hillierconsult.  Pressing Enter now gives me all the computers in that workgroup.

If I want to see a particular share on that network you need to know the computer on which that resides.  you can the do one of the following.
If you have the ip address then type in smb://192,168.0.2/<sharename> where 192.168.0.2 is the ip address of the machine.
Alternatively if you know the name of the computer type that in as smb://<computername>/<sharename>
so on my server I might type in smb://server/common to look at all the common public files.

Hope this helps

---

### Post by boriquajake on 2008-01-03
> **SteveHillier said:**
> I will try to translate.  
On the menu bar click 'Places' and then 'Computer'.
You are now in Nautilus.

In the location bar type in smb://<thenameofyourworkgruphere>

My workgroup is hillierconsult so I type in smb://hillierconsult.  Pressing Enter now gives me all the computers in that workgroup.

If I want to see a particular share on that network you need to know the computer on which that resides.  you can the do one of the following.
If you have the ip address then type in smb://192,168.0.2/<sharename> where 192.168.0.2 is the ip address of the machine.
Alternatively if you know the name of the computer type that in as smb://<computername>/<sharename>
so on my server I might type in smb://server/common to look at all the common public files.

Hope this helps

Wow, apparently you are fluent in "n00b" because I understood everything. Now, from nautilus is it possible to see the printers that are connected to the workgroup?

---

### Post by dannyboy79 on 2008-01-03
well it appears that he's explained it much easier than I did. I use the terminal to troubleshoot many things as you can't always tell what the error is through nautilus. it appears as though you got it working. If you're printer is gone from when you try to print, you need to re-add through the system, admin, printing tab. then add the smb printer again.

---

### Post by metoor30 on 2008-01-03
> **boriquajake said:**
> 
I feel like an idiot.

You shouldn't feel like an idiot.  Everyone has to start sometime.  The most powerful way to do anything on a Linux machine is to use the "Terminal" or Command Line.  This is in Menu(Start)/Accessories/Terminal.  All the commands in this post can be issued in a terminal.  If you really want to understand Linux, pick up a book that explains the OS through the command line.

---

### Post by disturbed1 on 2008-01-03
> **SteveHillier said:**
> I will try to translate.  
On the menu bar click 'Places' and then 'Computer'.
You are now in Nautilus.

In the location bar type in smb://<thenameofyourworkgruphere>

My workgroup is hillierconsult so I type in smb://hillierconsult.  Pressing Enter now gives me all the computers in that workgroup.

If I want to see a particular share on that network you need to know the computer on which that resides.  you can the do one of the following.
If you have the ip address then type in smb://192,168.0.2/<sharename> where 192.168.0.2 is the ip address of the machine.
Alternatively if you know the name of the computer type that in as smb://<computername>/<sharename>
so on my server I might type in smb://server/common to look at all the common public files.

Hope this helps

:guitar:

Thanks for doing the leg work for me :D.

---

### Post by boriquajake on 2008-01-03
You people are freaking geniuses!!:):)

---

### Post by Maricaibo on 2008-01-03
Not solved and I'm beginning to drown in information.

Finally got my VIA wirless module installed yesterday. At first I could see other wireless nets on my block. Could NOT connect to 2Wire router wirelessly. And now my Windows network has vanished. I could connect to the other computers on my LAN but no longer, even using 'Nautilus' and the SMB command.

Sigh...what to do now? I am getting really tired of reloading Ubuntu to try to get it working! If it weren't for trying to get MythTV built on this I'd just install WinXP here and be done with it- but gawd I loath M$oft!

HELP!

---

### Post by dannyboy79 on 2008-01-03
> **Maricaibo said:**
> I am getting really tired of reloading Ubuntu to try to get it working! If it weren't for trying to get MythTV built on this I'd just install WinXP here and be done with it- but gawd I loath M$oft!

HELP!
i hope you're not saying that you keep reinstalling ubuntu. That's not neccessary. Well get you squared away. First things first. Are you using gutsy or feisty? Since you posted this question within this thread I am going to help with your samba issue (not seeing windows network) and that's it. You should start another thread for your wifi adapter issue. Are you saying that you used to be able to see your windows network when you were using the ethernet card and not the wifi connection? please post the output of these commands

lsusb

lspci

enter them into a terminal session and paste back whatever the output is. I need to see what chipset your ethernet adapter uses.

What does this command return?

smbtree

findsmb

Don't enter passwords if they ask, if they do ask and your username is the same on your windows machines as your ubuntu machine, then enter the password for a windows machine on your network.

This is also assuming that you have an ip address and you can ping the other machine (disable machines firewall or allow it to accept pings from local network)

Do you have samba running?

ps aux | grep mbd

should return similar results.

root      5851  0.0  0.0   6044  1312 ?        Ss    2007   0:01 /usr/sbin/nmbd -D
root      5854  0.0  0.1   9432  2796 ?        Ss    2007   0:01 /usr/sbin/smbd -D
root      5873  0.0  0.0   9432  1208 ?        S     2007   0:00 /usr/sbin/smbd -D

If you don't need samba installed and only want to view shares on other windows computers than at a minimum you need smbfs installed.

have you tried what the previous poster stated about using nautilus location bar and enter in smb://ipaddress/share?

---

### Post by SteveHillier on 2008-01-04
> **boriquajake said:**
> You people are freaking geniuses!!:):)

I deny that accolade.

Just remember an expert is someone from out of town who knows slightly more about the subject than his audience.

That means ordinary mortals like me can seem to be experts or even geniuses occasionally.

---

