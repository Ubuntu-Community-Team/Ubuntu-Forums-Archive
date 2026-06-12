---
title: "can't connect to ubuntu from windows through network, just a username and pass issue"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by MetalRampage on 2007-09-09
I have recently connected a ubuntu pc to a windows workgroup, samba of course. They are all on the same workgroup. The ubunto pc is finally able to connect and access all network resources, shared folders, printer... I set up a folder to share on my Ubuntu pc. All of my windows workstations recognize that my Ubuntu pc exists, and it seems as though I should be able to access it no problem. Here's the problem though, it asks me for a username and password. I tried all sorts of variations of what I know is the right username and pass that I use to sign in to the Ubuntu workstation, but nothing works.

I am a total noob to linux. If you tell me to put some commands in smb.conf, then tell me how to edit it, I can only open it as a read only document and can't save anything. If you tell me to run some command, please tell me where I type it in.

I've already searched all over the forums, but I just... can't seem to find my way around here.

Many thanks,
MetalRampage

..btw 7.04 fiesty fawn, other systems are winxp and win2k, and I tried posting on the noob forums, but I didn't have any luck there

---

### Post by Irony on 2007-09-09
This is my entry in my /etc/samba/smb.conf file;

[PHP][share]
        comment = ext3system
        path = /media/hda9/shared
        writeable = Yes
        guest ok = Yes[/PHP]

This is on an ext3 partition. I tried it on a fat32 partition but it needed a username and password to get into it - for some reason this happens on Ubuntu but not PCLinux.

It is important to make sure that the /media/hda9/shared folder in my example has permissions to allow users to access it - the folder permissions supersede those written in the smb.conf file. I can't remember if I set the permissions (via gksudo nautilus) when it was connected or prior; just try either way to find out.

Note after changing the file do;

[PHP]sudo /etc/init.d/samba reload

sudo /etc/init.d/samba restart[/PHP]

---

### Post by MetalRampage on 2007-09-09
I don't think that begins to answer my questions. Look, I already have a folder shared, though the administrative tools. And I have no idea where I'm supposed to type in the sudo command.

---

### Post by Wiebelhaus on 2007-09-09
He answered your question but assumed you've learned the basics, look,  this is how I do it.


to access the command line Applications>accessories>terminal

Check sig for website on it.


 > [QUOTE]make windows able to access ubuntu shared files

First install samba

sudo apt-get install samba

With this you will have samba installed on your system, now you need to edit the configuration file which is located at:

/etc/samba/smb.conf

Here I will put a simple minimal configuration to allow share files from your Linux server.

 

[global]

workgroup = MSHOME

netbios name = UBUNTU_SERVER

security = SHARE

auth methods = guest

domain master = No

wins support = Yes

[share1]

comment = mi home

path = /home/USERNAME IN LOWERCASE

 

read only = No

guest ok = Yes

 

 

    * workgroup; Lets you specify the windows workgroup
    * netbios name; Lets you specify the name with your Linux PC will be seen by windows PCs
    * security; specifies the level of security, default is user, but if the users on the windows PCs are not the same as the ones on the Linux PC, you better use share instead
    * auth methods; Possible options include guest (anonymous access), sam (lookups in local list of accounts based on netbios name or domain name), winbind (relay authentication requests for remote users through winbindd), ntdomain (pre-winbindd method of authentication for remote domain users; deprecated in favour of winbind method), trustdomain (authenticate trusted users by contacting the remote DC directly from smbd; deprecated in favour of winbind method)
    * domain master; Lets you configure your PC as a domain master or not, in this case we prefer not, as our goal is only to share files
    * wins support; If you want or not to have wins enabled or not

Now comes the shares section, the string you put between the [] will be how windows will sees the share, in this case share1

      path; You put here the path you may want to share

      read only; yes or no, depending if you want to permit other users to write on this directories.

      gest ok; It is a boolean field, and will permit or not guest users to access this resource

______________________________________________

For simple sharing that is all that is needed [/QUOTE]

that was stolen from somewhere can't recall , prolly ubuntugeek.

---

### Post by MetalRampage on 2007-09-09
I ALREADY HAVE SAMBA INSTALLED. Why does everyone tell me I need to install it, it's a part of the newest ubuntu.

I have the server running, other computers can see it, it can see and access other computers. IT JUST WON'T LET ANYONE IN TO IT.

I'm not trying to be rude here, it's just that most of what I'm being told is either redundant or it just doesn't apply.

By the way, you were right about the terminal, I'm sorry, but when I tried to run commands through the terminal last night nothing worked, just something like "unknown command: sudo". Seems to work now though.

I cannot make changes to the samba.conf for some reason, it is read only to me and tells me I don't have permission to alter it.

If I could alter it, it wouldn't be a problem, I'm sure I could work it out. 

Ok, clearly I was asking too much when I started posting here. I'll figure the rest out on my own, but please, please please JUST tell me how can I make changes to the samba.conf file. If you can tell me what login I need to use, or where I can change permissions or whatever, then I will, but please, just assume I don't know anything and help me make changes to the file.

Thank you very much

---

### Post by Wiebelhaus on 2007-09-09
the internet equivalent of yelling at me means , I'm not going to help nor are any of us obligated to.

you should [read this]("http://linux.oneandoneis2.org/LNW.htm") then re - install winblows.

---

### Post by MetalRampage on 2007-09-09
I have already apologized, and if you can't help me, I understand, but why would you give me information I didn't ask for? If you like hearing yourself talk that's dandy and all, but I don't take kindly to it. I know linux isn't the same as windows, but the two are compatible to an extent. Linux can see other pcs fine and vice versa, it's just a permission issue. I can just use my windows workstations to keep the shared files, and it looks like that's the way to go. Once again, I'm sorry to have offended you, but... if it's irrelevant to what I'm asking about... then... why do you post? You're right, you have NO OBLIGATION.

---

### Post by MarvinMartian on 2007-09-13
> **sx66gns said:**
> He answered your question but assumed you've learned the basics, look,  this is how I do it.

to access the command line Applications>accessories>terminal

Check sig for website on it.

that was stolen from somewhere can't recall , prolly ubuntugeek.

I found this while searching for a solution and I just wanted to express my thanks, as it helped me and was exactly what I needed to get it working.

Thank you!

---

### Post by maybeway36 on 2007-09-13
press alt+f2 and type:
```
gksu gedit /etc/samba/smb.conf
```
change
```
;  security = user
```
to
```
   security = share
```

---

### Post by insanity2k7 on 2007-09-13
maybeway36 -- Thanks dude!  I'm a total linux novice but am quickly becoming a convert.  Being able to make any and every change without rebooting is most awesome.  At any rate...

security = share

...fixed my problem, thanks!

MetalRampage -- If you're still around, hopefully you've worked through your "issues."

---

### Post by kubilaycan on 2007-09-16
i use feisty. i have the same problem. xp requires a username and password, and i have no idea what it is.

i changed my conf to security = share, and i restarted samba aswell, but still asks for username and password.

---

### Post by kubilaycan on 2007-09-16
solved: 

just followed this guide [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DNo.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DNo.29)

tip: look out for the semicolon before "security = share" in smb.conf. you have to remove it.

that was the culprit!

---

