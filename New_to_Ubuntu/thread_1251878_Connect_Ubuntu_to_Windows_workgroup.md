---
title: "Connect Ubuntu to Windows workgroup"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by hnarwan on 2009-08-28
Hi All,

I've just installed Ubuntu 9.04 - the Jaunty Jackalope on my Sony Vaio laptop (replacing Vista).

The problem i'm having is i'm unable to access my Windows xp workgroup (mshome) from this ubuntu laptop. 

I have installed Samba, changed my smb.conf file to change the workgroup to 'MSHOME'. I've pasted the global settings section below for reference.

Now when i go to places/network/windows network - i see MSHOME, but going into it i only see this ubuntu laptop 'hardeep-laptop'.

I have tried to connect from places\connect to server - by entering

Service type: Windows share
Server name: Wks001 (this is the windows xp computer i'd like to access)

When i click connect it prompts me for a username/password. The username field is already enterred for me with my username on the ubuntu laptop, so i put in my password for the ubuntu laptop but it throws an error about invalid username/password.

I've also tried entering my windows xp username/password - again i get the same error.

I can see the ubuntu computer from my windows xp machine but cant access it. I can ping between computers (i'm networked via a wireless router).

Any ideas?
 

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

---

### Post by dk06 on 2009-08-28
**[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)**
> 
**Note:** When Windows attempts to access a SMB share it will use the current Windows user name and password.  The map to guest = bad user trick above allows access to the public share only if you give Samba an incorrect user name. If you give it a valid user name, but a bad password, the login will fail and Windows will give you a password prompt when you try to access the share. If you have the same user name for your Windows machine and your Ubuntu machine, you could be unwittingly giving the Samba server a valid user name, but invalid password. To resolve this you will either have to change the Windows user name, or to remove that user name from the Samba password file with sudo smbpasswd -x [username]. 


[http://www.europe.eclipse.co.uk/Ubuntu/810%20on%20Win%20Network.htm]("http://www.europe.eclipse.co.uk/Ubuntu/810%20on%20Win%20Network.htm")
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://ubuntuforums.org/showthread.php?t=340386](http://ubuntuforums.org/showthread.php?t=340386)


And for NFS,
[http://www.windowsvistaplace.com/enabling-nfs-in-ubuntu/othersoftware/](http://www.windowsvistaplace.com/enabling-nfs-in-ubuntu/othersoftware/)
[http://ubuntuforums.org/showthread.php?t=310168](http://ubuntuforums.org/showthread.php?t=310168)

---

### Post by hnarwan on 2009-08-28
Hi Dk06,

Thanks for the reply, i've created an account with the same username/password on my xp machine as the one i have active on my ubuntu laptop. I still hit the same problems when trying to access.

So if i have samba installed on my ubuntu machine, have modified the smb.config file to point to the windows workgroup which i want this ubuntu laptop to access what else do i need to do?

thanks again.

Hardeep

---

### Post by theozzlives on 2009-08-28
Did you install samba by ```
sudo apt-get install samba
```?

---

### Post by Moop on 2009-08-28
I think it's beneficial to change the workgroup name on XP to "workgroup." Vista and Win7 both use workgroup and Ubuntu starts with it as the default name. Using MSHome just confuses things.

---

### Post by hnarwan on 2009-08-28
Thanks guys.

I've renamed my xp workgroup to 'WORKGROUP', the only thing is i'm unsure how to change this value in smb.config because it says i dont have permissions.

I did install Samba using sudo apt-get install samba, i think it may be worthwhile to de-install/re-install so the config file has the default 'workgroup' value but i'm unsure how to do this?

---

### Post by Moop on 2009-08-28
I'm not an expert but I've never had to install any extra samba stuff to access my windows workgroup. Ubuntu does that out of the box. I've certainly never had to mess with any samba conf file.

---

### Post by hnarwan on 2009-08-28
that's what i thought Moop, the last time i installed Ubuntu (the first time last year) i dont remember playing around with anything to get access to my windows workgroup.

I'm completely lost as to what i'm supposed to be doing to see my xp computer from this ubuntu laptop :(

---

### Post by Moop on 2009-08-28
I just go to Places-Network and it shows Windows Network. If I click on that I get my different windows machines. 

You should restart networking on Ubuntu after you make changes to it or the windows pc. 

I'm not sure but I think file sharing needs to be enabled on the XP machine. 

```
sudo /etc/init.d/networking restart
```

---

### Post by mapes12 on 2009-08-28
> I'm not sure but I think file sharing needs to be enabled on the XP machine. Spot on!

You need to go into Control panel in XP and enable "File and print sharing". Then go to the folder you want to share. Right click and enable "sharing". If the user account where the share is located in XP is a Limited account then you may have problems. The account needs to be given Administrator permission. Bad security but that's not my fault.

Also, you don't need a full blown Samba configuration and editing all that samba.config stuff. You can make the whole thing work using the simple pyNeighborhood GUI from Synaptic.  Renaming you Workgroup is irrelevant. The "Scan" function in pyNeighborhood will find it (provided you have the share stuff on XP configured as above). 

There are many pyNeighborhood HowTo's out there. If you want mine post back.

---

### Post by hnarwan on 2009-08-28
Thanks both,

I've actually got File and Printer sharing enabled on my xp computer (i can browse shares on that machine from other computers without a problem (albeit other windows machines).

I also have 'Use simple file sharing (recommended) checked in folder options. 

I'm pretty sure it's not a setup issue on my xp side but something i've missed or screwed up in Ubuntu.

So if i currently have a workgroup named workgroup running on my xp computer, with file sharing enabled, what do i need to do exactly on Ubuntu?

also Should i remove Samba if it's not needed? How would i do that?

---

### Post by mapes12 on 2009-08-28
> also Should i remove Samba if it's not needed? How would i do that?Locate it in Synaptic then mark it for complete removal. Apply the changes and away it goes.

---

### Post by hnarwan on 2009-08-28
thanks Mapes.

Any ideas about what i need to check on Ubuntu to try and get the connection to my windows workgroup going?

I'm completely lost here.

It's basically a new install, the windows workgroup is setup correctly so what configurations do i need to play around with on Ubuntu to make this work?

I'm also having a hard time getting dvd's to play and my usb flash drive to work, hopefully i can get through those problems or i'm going to be crawling back to windows i think.

---

### Post by mapes12 on 2009-08-28
> **hnarwan said:**
> thanks Mapes.

Any ideas about what i need to check on Ubuntu to try and get the connection to my windows workgroup going?

I'm completely lost here.

It's basically a new install, the windows workgroup is setup correctly so what configurations do i need to play around with on Ubuntu to make this work?

I'm also having a hard time getting dvd's to play and my usb flash drive to work, hopefully i can get through those problems or i'm going to be crawling back to windows i think.

DVD's - Go to Synaptic and install ubuntu-restricted-extras then to make sure you have every codec there is to support play back go [here]("http://www.medibuntu.org/") and follow the instructions which is basically cut and paste stuff into Terminal

USB Flash Drive - Haven't got one so don't know. Suggest you post a separate thread.

Accessing windoze boxes - If you're sure you have the Sharing stuff right on the windoze boxes (and in my experience windoze sometimes reports stuff as being shared when it isn't! and it took me 3 days to work out why) then I would install pyNeighborhood. Some tweeks to set it up. Once installed go to Edit>Preferences. Set the mount point to /home/yourusername (this means you don't need root hassle to connect). Tick the box Romove mount points after unmount. This makes things clean after your network session. In the File Managers tab click add then add "nautilus". The default xterm thingy looks horrible!

Back to the main GUI. Left hand panel right click Scan to find your windoze shares. Well at least that worked for me. I say again, if you have problems then 9 times out of 10 it will be with the windoze boxes, not Ubu.

---

### Post by hnarwan on 2009-08-28
thanks Mapes, so you've helped me resolve the dvd playback issue. That's one less thing to worry about. I'll post a new topic for my flash drive issue, basically the drive shows up but when i double click it i get 'unable to mount drive' or something to that effect.

As for my main issue, i installed the application you mention, made the changes specified but again i only see this ubuntu laptop in the list under mshome where i would expect to see my xp machine.

I'm not sure what else to check on my windows machine, it lets other xp computers connect, i never had any issues with vista when that was installed on this laptop but after installing ubuntu on this laptop i'm unable to access or even see that machine.

If you or anyone can guide me through checking anything else that could be to blame i'd be grateful as always.

---

### Post by mapes12 on 2009-08-28
How many user accounts do you have on the XP machine?

Are we talking about just one XP machine or are there others?

The laptop you are trying to connect _from_ is running Ubu. Correct or wrong?

---

### Post by mapes12 on 2009-08-28
To try and help you out some more I've taken a screen shot of how pyNeighborhood looks on my machine. To start with I set up pyNeighborhood how I described previously. Then I R/C  Groups and it immediately found BT (my router) MSHOME (my workgroup for my own XP box) and HOME (which is the workgroup with the kids machines).

D/C MARK and I get the result in the R/H panel. D/C My Document and it gets mounted. Then if I R/C it I can select Nautilus and browse it including transfering files back and forth.

As I mentioned before it took me 3 days to get this working but the issue was with XP _not_ Ubu.

---

### Post by hnarwan on 2009-08-28
Thanks Mapes, i appreciate all your efforts.

Basically right now i have two xp computers, one which i really need to connect to from my ubuntu machine, the other xp computer can connect to my first xp computer without any problems, that too is a laptop connecting over the wireless router connection.

I now have two accounts on my xp computer, one i created today which has the same username/password as that of my ubuntu pc, (it's also an admin account).

When i check pyNeighborhood i can see my MSHOME network, but it only lists my ubuntu laptop. 

I've been browsing the web for solutions for most of the day but i havent really got anywhere.

---

### Post by mapes12 on 2009-08-28
Could you post a screen shot to take a look please?

EDIT - > I now have two accounts on my xp computer, one i created today which has the same username/password as that of my ubuntu pc, (it's also an admin account).OK. Try creating some shared folders for _each_ of these accounts then run the pyNeighborhood scan again. BTW the username and password on XP being the same as Ubu will not be relevant.

---

### Post by hnarwan on 2009-08-28
hi Mapes,

I've attached the screenshot which shows i can see the MSHOME network but only the ubuntu machine being listed.

Let me know if you can see anything obviously wrong or if you think i could try anything out to get this working.

---

### Post by mapes12 on 2009-08-28
What happens when you D/C Hardeep Laptop in the R/H panel?

---

### Post by Moop on 2009-08-28
I can't figure out why your Ubuntu laptop would be listed under MSHome. Are you sure that's not your XP laptop with the same name?

---

### Post by mapes12 on 2009-08-28
> **Moop said:**
> I can't figure out why your Ubuntu laptop would be listed under MSHome. Are you sure that's not your XP laptop with the same name?
I think the OP has given the UBu machine the same name as the XP machine. Given that the machine reported in the screenshot is under MSHOME this is undoubtedly the XP network trying to be accessed. Duplication of the name in Ubu is irrelevant.

Repeat: What happens when you D/C Hardeep Laptop in the R/H panel?

---

### Post by hnarwan on 2009-08-28
Mapes you're a genius, i added pc1 (my xp pc) manually in pyNeighborhood and it's working!

thanks so much!

---

### Post by mapes12 on 2009-08-28
> **hnarwan said:**
> Mapes you're a genius, i added pc1 (my xp pc) manually in pyNeighborhood and it's working!

thanks so much!Happy to help :)

Not so long ago I was clueless with Ubu. It was only by giving things a go and more importantly testing stuff on my machine that I learned how to make these applications work. It won't belong before you will be doing the same .....  :lolflag:

---

### Post by hnarwan on 2009-08-28
Thanks again Mapes, i was honestly thinking of quitting and going back to windows but i think i'll give it a proper go before i make that decision.

I assume you're all sold on the Linux versus Windows debate? I use my computer for the usual thing, office apps, internet, music, video's etc, i switched to Linux as my vista installation on this laptop died and i wanted to get the thing back up and running without buying a new windows cd (i lost my restore cd).

So far my experience of linux hasnt been too bad but to be honest i am kinda missing what all the hype is about.

It's not that much faster than windows and you need to play around with stuff a lot more, i'm not really seeing the payoff for that work.

For example now with your help i've managed to get access to my movie share file but playing movies with vlc on ubuntu doesnt seem as stable as it was on vista (the screen closes by itself sometimes, and hangs often).

I hate to sound like one of those windows knobs but i wanted to throw my opinion out there so someone could put me straight.

Anyway i'm going to give it a real chance, over the next month of so and see how i get on.

thanks again for all your help.

have a great weekend.

---

