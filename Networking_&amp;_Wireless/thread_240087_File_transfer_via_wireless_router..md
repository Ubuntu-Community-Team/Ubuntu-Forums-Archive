---
title: "File transfer via wireless router."
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by insane_alien on 2006-08-20
Ok, first off. i suck at networking. I've never had to do much to do with networking so i don't know a lot about it.

My friend has a couple of movies on his laptop(we made them so they're not pirated)neither of us has a crossover cable but i have a wireless router for my laptop. we tried to transfer the files using windows but that just wouldn't happen. so i'm wondering how i would do this using ubuntu. i have dapper installed on my machine but he only has XP despite me shamelessly plugging linux at every oppertunity. so is there a live CD(ubuntu or otherwise) that would allow us to transfer the files? 

normally this would be a sneakernet job but we don't have any otherway of getting the files off his lappy.

---

### Post by neouser99 on 2006-08-20
still need help?

-neo

---

### Post by tturrisi on 2006-08-21
how big are the files?  You could burn to cd or dvd or use a usb stick.

---

### Post by insane_alien on 2006-08-21
about 15 GB of files. only have a 128MB mem stick and his lappy has no burner.

---

### Post by harisund on 2006-08-21
> **insane_alien said:**
> ....but i have a wireless router for my laptop. ...

What does this mean? How can a laptop have a wireless router in built? 

Do you mean you have a wireless router which your laptop can connect to? 

Assuming that is so, and assuming the other computer also connects to the wireless router, you can easily transfer files. 

So here are my questions: 

1. Is there a wireless router, and can both computers access it? 
2. Does either machine have access to internet?

---

### Post by insane_alien on 2006-08-21
ahh yeah looking back at that bit it is a bit vague. i have a wireless router so my laptop can connect to it around the house. the laptop we need to copy from has a wireless connection as well.

1. Yes.
2. via the router, yes.

---

### Post by harisund on 2006-08-21
Ok cool. Let's assume your Linux box is 192.168.0.2, the Windows box is 192.168.0.3, and the router is 192.168.0.1. Both the Windows box and the Linux box are connected to the itnernet. 

And I am guessing you are somewhat familiar with the command line. 

So on the linux box, open a terminal and execute
```
sudo apt-get update
sudo apt-get install proftpd
```

It will ask you if you want a stand alone installation or a 'inetd' installation. Choose stand alone. 

Now, go to your Windows box. Open a explorer window, and in the address bar type in [ftp://192.168.0.2](ftp://192.168.0.2) (Linux box IP). It should ask for user naem and password. Enter the user naem and password of the user to whose home directory you want to copy the files from Windows to. 

Then that explorer Windows should show you the contents of the Linux username's home directory. Then it is a simple matter of opening another Explorer windows and drag/drop or copy pasting the contents

There are plenty of other ways to do file transfer, but FTP is the easiest since installing a FTP server on Ubuntu is straight forward, and a FTP client is installed on Windows XP.

---

### Post by insane_alien on 2006-08-21
wow that looks pretty easy. i'll try it now.

---

### Post by insane_alien on 2006-08-22
ok, it didn't work. i didn't get a login window just an error saying 'windows does not have permission to access this folder' i chose standalone version of proftpd.

---

### Post by harisund on 2006-08-22
Ok try one thing. Within your Linux box, on a command line execute 'ftp localhost'. Hopefully it should connect and you should be asked for a username and password. Login with your own username and password, and check it if works. 

Once you have ensured that ftp works on the localhost, you have to check for your firewall. Do you have any firewall enabled? 

Finally, go to your Windows box. How did you try to access FTP? 

We will give this one more try (after following the above steps, that is) and if not I will walk you through Samba, though I don't really see a reason why this wouldn't work.

---

### Post by insane_alien on 2006-08-22
ok, i opened the FTP ports in my firewall but it still gives the error.
FTP ports are 20 and 21 aren't they?

I tried to access the FTP through an explorer window. i opened up my documents and used the address bar on that.

---

### Post by Useless on 2006-08-22
how about using a combination of openSSH on the linux box and connecting to it using WinScp and just dumping the files.  When connecting to it, use your linux account credentials and just dump them in your home directory.

---

### Post by insane_alien on 2006-08-22
Ummm.. en englais, sil vous plait.

i honestly didn't understand that at all Useless. harisund is doing a good job of explaining things, maybe he could translate.

---

### Post by harisund on 2006-08-22
Ok, what useless has said here is just another method of file transfer, which also we will eventually get to, if nothing else works. 

Fine, now that FTP seems ruled out for some reason, let's proceed with other techniques. The next one we will use is called Samba. 

First off, when you said you opened port 21 your firewall, what firewall did you mean? If you meant your router (external, or hardware firewall), close it. Since both the Windows and the Linux boxes are behind the router (meaning on the LAN), opening up port 21 would mean anybody from the other side of the router (on the internet, like me for example) could access your machines on port 21. 

Anyway so let's uninstall proftpd. Execute 'sudo apt-get --purge uninstall proftpd' and proftpd will be out of your system. Now execute 'sudo apt-get install samba smbfs' and let it install. 

Once you are done with that, you will need to edit the file /etc/samba/smb.conf. Of course you will need to edit it as root. Use sudo appropriately. Keep scrolling down  until you find a section beginning with [Homes]. The file is well commented, so you shouldn't have any difficulty finding it. 

Under that section, you will find something called 'Writeable=no'. Change it to Writeable=yes and make sure there is no '#' in the front (which means it is a comment). 

Once that is done, save the file. Now, let's assume lin is the username on the linux box. Execute 'sudo smbpasswd -a lin' and enter a password. This could be the same as lin's login password if you wish, for convenience. 

Once this is done, restart your samba by executing 'sudo invoke-rc.d samba restart' 

Now head to your Windows machine. Let's assume the linux box has an IP of 192.168.0.3. Open an explorer window, type in ```
\\192.168.0.3
```. Now your Windows box will ask you for a username and password. Enter lin and the password you entered in the previous step (the result of smbpasswd step). You will then be shown the lin's home directory, and if you had followed the earlier 'writeable=yes' step, you will be able to write into the directory as well. 

Of course, this assumes a few things. One, both your Windows and Linux box are on the same subnet. If you dont' understand, just make sure both boxes connect to the router, and their IP addresses differ just in the last set (as in 192.168.something-common.something-unique). 

The reason I use 192.168.*.* is that most home wireless routers hand out IP addresses in that format. 

The next assumption is you don't have a software firewall on your Linux box. This is typically iptables. If you have never heard of terms like 'iptables' or 'shorewall' or 'firestarter' then it is very likely that you haven't messed with it, so you should be safe. If on the other hand for some reason these terms are familiar, or you have encountered them before (as in some software requested some changes to be made with the above) then we might have to modify your firewall (software) to allow transfers.

The reason I have not yet come to SSH (the option suggested by Useless above) is that SSH encrypts everything. While it may be an excellent option for remote file transfers between machines on the internet, on your home network you don't need that high level of encryption, and becase everything is encrypted, file transfers are very slow, especially if you go to range of gigabytes. 

I am expecting Samba to work fine. If it doesnt we will just SSH.

---

### Post by insane_alien on 2006-08-22
i only opened the ports on my software firewalls on my windows machine. both windows firewall and another firewall i got from my university.

both computers are on the same subnet.

now i don't get an error but i get a IE window with the results of a search for the ip address.

this is probably a problem with my windows box. could a live CD do this because i only need to read off the ntfs filesystem. and the files are quite big so the SSH doesn't sound so attractive. but if thats what it takes then so be it.

---

### Post by harisund on 2006-08-22
Wait, you will only get a IE window if you had entered '//' instead of '\\'. 

Also, open up a command prompt in your Windows box, and enter 'ping 192.168.0.83' (substitute appropriately with Linux box) and see if the Windows box can see the Linux box?

---

### Post by insane_alien on 2006-08-22
I GOT IT! i was bored so i went bck and tried the ftp thing again and for some reason it worked(maybe samba install changed something?) 

thanks for all your help harisund. hope i wasn't too much of a PITA.

yeah with the samba thing turned out i was using the wrong slash(D'oh)](*,)

---

### Post by harisund on 2006-08-22
Ok, so both Samba and FTP worked? Just confirming ... 

and no no, not at all a PITA.. glad to be of help :)

Also, on the firewall issue, if you are moving stuff from the Windows machine to the Linux machine or if you are using the Windows machine to copy and paste from the other box (such as using samba or ftp) then you typically wouldn't need to open any ports on the Windows machine. If you are trying to do anything funny, Windows firewall will pop up a message box and say "FTP (or whatever) program is trying to access the internet. Should I allow it?" Clicking on yes will automatically configure the WIndows XP firewall to allow that particular service. 

You wouldn't need to open port 21 on your WIndows server unless you are installing a FTP server on your Windows box (which would have been another option I could have walked you through, but this is not a Windows forum, so let's stick to modifying Ubuntu :) )

---

### Post by insane_alien on 2006-08-22
Yeah, i didn't want to mess with windows. its just too easily crapped up. i tried to do it all through XP before and looked through about 30 forums before i got an answer better than 'pfft n00b' and then it was all 'download this file and stick in the system folder' a bit dodgy. spent a month trying it that way.

2 days here and its all peachy.

---

