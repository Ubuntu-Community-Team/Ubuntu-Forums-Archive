---
title: "Samba configuration help"
date: 2021-10-20
forum: Networking &amp; Wireless
---

### Post by fjl05 on 2021-10-20
Perhaps this is something easy but I cant seem to figure it out. I'm trying to make a single share service folder that when the user enters that folder(My Folder) it automatically takes them into a folder named after the users login name and to have it set to use the specific parameters set for that folder. So here is an example of what I have written to smb.conf and what I am trying to do.

[Mario]
comment = Mario's Folder
path = /Users/U%              <<<this sends the user 'Mario' into a folder named /Mario, or basically their username.
browseable - no
valid users = Mario, Toad, Yoshi

[Luigi]
comment = Luigi's Folder
path = /Users/%U                <<<this sends the user 'Luigi' into a folder named /Luigi, or basically their username.
browseable = no
valid users = Luigi, Bowser, Peach


[My Folder]
comment = %U home directory
browseable = yes
copy = U%          <<<theoretically this should copy the same parameters from the service named after the user [Mario] or [Luigi] but it doesnt work.


I'm trying to make it so there is only one network folder called 'My Folder' and entering it takes the user directly to their own mostly private folder. Basically 'path' is set to redirect the user that is login in to a folder named after their username. the %U replaces itself with the name of the user login in. This works perfectly for 'path'. So for example if I login with Mario it will replace /Users/%U to /Users/Mario and send me into that folder. If where I to login with Luigi then it would take me to /Users/Luigi. So the %U as a variable works.

The problem I am having is using %U variable for the 'copy' parameter. It doesn't seem to like %U variable. The 'copy' command lets you copy parameters from another service such as [mario]. Without the 'copy' command then i dont inherit the correct parameters I need from [mario] and end up not having any writing permissions when entering the folder through 'My Folder'. If I manually add in (copy = Mario) to the [My Folder] service, then it will inherit all the parameters from [Mario] and work exactly like I need it to. But then if Luigi logs in it will get wrong set of parameters, the [Mario] parameters which are different from [Luigi]. So the problem is that I cannot get 'copy' to use %U variable. How do i fix this?

---

### Post by TheFu on 2021-10-20
Why not use the [homes] special stanza to provide access by username for each user's HOME directory?


```
[homes]
  comment = Home Directories
  hosts allow = 127.0.0.1 172.22.22.0/24  
  hosts deny = 0.0.0.0/0
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
  valid users = %S
```

---

### Post by fjl05 on 2021-10-20
Hmm... Ok thanks I"ll try it later today and see if I can get it to work and report back.

---

### Post by rsteinmetz70112 on 2021-10-21
If you want to specify a different folder you can put that in the share with 
```
path = /some/directory/%U
```
It s usually and by default ```
path=/home/%U
```
Actually there are a number pre-defined of variables you can use.
I actually have my [homes] point to a different server from my login server.

---

### Post by TheFu on 2021-10-21
> **fjl05 said:**
> Hmm... Ok thanks I"ll try it later today and see if I can get it to work and report back.

I almost always specify these settings for each share stanza:
```
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
```
I might make the masks a little more restrictive, 640 or 750, but I always want to control the owner, group and other permissions.

However, these days we only use samba to share HOME directories to the users on the system that have no other choice.  Most users have Linux workstations and use NFS to access the storage on our LAN. Samba/CIFS is for Windows-only.  NFS provides native permissions control and with NFSv4.x, there are some great performance tuning options to make it much faster.

---

### Post by fjl05 on 2021-10-21
I've been having problems with the 'create mask' parameter like 'create mask = 755' does not come out as 755. I was reading up on it and mentions something about security or something that honestly goes above my head. But then I also learned of the 'force create mode' which does in fact work. But what exactly is the point of having two of these and using one that doesn't really do what its supposed to and what does it have to do with security? should I not be using 'force create mode'?

---

### Post by TheFu on 2021-10-22
> **fjl05 said:**
> I've been having problems with the 'create mask' parameter like 'create mask = 755' does not come out as 755. I was reading up on it and mentions something about security or something that honestly goes above my head. But then I also learned of the 'force create mode' which does in fact work. But what exactly is the point of having two of these and using one that doesn't really do what its supposed to and what does it have to do with security? should I not be using 'force create mode'?

Try 
```
create mask = [COLOR="#FF0000"]0[/COLOR]755
```

While chmod works with only 3 or 4 of the 4 octal values, I think Samba requires all 4.  Doesn't my example show 4 octal values? It should if it doesn't.

---

### Post by Morbius1 on 2021-10-22
> I've been having problems with the 'create mask' parameter like 'create mask = 755' does not come out as 755.

May I ask what resulting permissions you do get?

And may I also ask why you want new files to be executable?

As a side note: I changed my create mask value on your other question ( [https://ubuntuforums.org/showthread.php?t=2468194](https://ubuntuforums.org/showthread.php?t=2468194) ) but if there is an issue here there might be an issue there.

---

### Post by fjl05 on 2021-10-22
> **Morbius1 said:**
> May I ask what resulting permissions you do get?

And may I also ask why you want new files to be executable?

As a side note: I changed my create mask value on your other question ( [https://ubuntuforums.org/showthread.php?t=2468194](https://ubuntuforums.org/showthread.php?t=2468194) ) but if there is an issue here there might be an issue there.

I end up getting 744 as the permissions. And the reason I want them as executable is because it was part of my test try from the other thread to get the results of owners adding things and no one being able to delete things but the owners. But it isn't just so much about that. Its about things not working how they should. I tell it to do something and it just doesnt want to. That just further complicates things that are already complicated. Much like the first problem I mentioned when starting this thread, which I still need to test try actually. Basically it just frustrates me when things dont work like they should. 

1+1 should = 2 but instead equals 3.1415926535897932384626433832795. Like, just why?

---

### Post by fjl05 on 2021-10-22
> **TheFu said:**
> Try 
```
create mask = [COLOR=#FF0000]0[/COLOR]755
```

While chmod works with only 3 or 4 of the 4 octal values, I think Samba requires all 4.  Doesn't my example show 4 octal values? It should if it doesn't.

I tried *create mask = 0755 *I still got an output of 744 permissions -rwxr--r--.
Only **force create mode** seems to do the trick. I still dont understand why 'create mask' is limited and doesnt allow me to do exactly what I need. Whats the point of that? I tried reading up on it, but the jargon goes over my head.

---

### Post by TheFu on 2021-10-22
> **fjl05 said:**
>  1+1 should = 2 but instead equals 3.1415926535897932384626433832795. Like, just why?

Unless 1+1 is just under 4, for "very large values of 1". ;)

I've not seen the issue described. My only guess would be that there are either ACLs preventing the mask or that the underlying file system isn't POSIX i.e. not a native Linux file system. All bets are off when exFAT or NTFS or HPFS are used.

**df -Th** is a very helpful command, BTW.

---

### Post by Morbius1 on 2021-10-22
> 1+1 should = 2 but instead equals 3.1415926535897932384626433832795. Like, just why?
Your calculation is correct but you are using the wrong base. 1+1 should equal 1.

A new file will come to samba with permissions of 777. Three other parameters are in play here ( map archive , map system, and map hidden ) that turns that into 766. In binary that is 111 110 110.

A "create mask" is converted to binary and then a logical AND is performed on the original permissions passed.
If we use a create mask value of 664 it's binary equivalent is 110 110 100

In a logical AND if both numbers are 1 the answer is 1. If one number is 0 the answer is 0. So what we have is:

111 110 110
110 110 100
========
110 110 100 which is octal 664

So let's do the same thing with a create mask of 755 which is 111 101 101:

111 110 110
111 101 101
========
111 100 100 which is octal 744.

A "force create mode" is similar but it does a logical OR on the result ........

---

### Post by fjl05 on 2021-10-22
> **TheFu said:**
> Why not use the [homes] special stanza to provide access by username for each user's HOME directory?


```
[homes]
  comment = Home Directories
  hosts allow = 127.0.0.1 172.22.22.0/24  
  hosts deny = 0.0.0.0/0
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
  valid users = %S
```

Ok I tried it and it seems to work! Thanks!

 The problem i'm having is *I dont understand any of it*. And why it works. I dont like to just add some configuration code and not understand what its doing. I tried reading up on it at the [homes] section on the samba website here, [https://www.samba.org/samba/docs/current/man-html/smb.conf.5.html](https://www.samba.org/samba/docs/current/man-html/smb.conf.5.html)
But like much everything else, It goes over my head and I cant understand what its trying to say. Can someone explain it like I am an idiot. Which I obviously am..

Also I've condensed the service down from this;


```
[homes]
  comment = Home Directories
  hosts allow = 127.0.0.1 172.22.22.0/24
  hosts deny = 0.0.0.0/0
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
  valid users = %S

```

To this.
```
[homes]
  comment = %Us Home Directory
  browseable = yes
  guest ok = no
  writable = yes

```

And it still does what I need. I mostly understand what **hosts allow/deny** do. But do I really need them for this to function properly? Why did you add those? And what about **valid users = %S**. What is that supposed to do here? According to the samba website, I read that *%S = the name of the current service,* *if any*. But why would you need the name of the current service here? Whats its function in this case?

Also is there a way to rename the [homes] service so its says something like *My Folder *instead of *homes*?

---

### Post by fjl05 on 2021-10-22
> **TheFu said:**
> Unless 1+1 is just under 4, for "very large values of 1". ;)

I've not seen the issue described. My only guess would be that there are either ACLs preventing the mask or that the underlying file system isn't POSIX i.e. not a native Linux file system. All bets are off when exFAT or NTFS or HPFS are used.

**df -Th** is a very helpful command, BTW.

I'm actually running Ubuntu Server on a Raspberry Pi. Everything is currently EXT4. I did try mounting some external drives, exFAT, NTFS even FAT32 and that just gave me a whole bunch of wacky glitches. But I realized I first need to properly learn the ins and outs of SAMBA before I start dealing with the errors that come up when using it with mounted external drives. So once I learn SAMBA properly, I will then tackle head on those wacky glitches. My final plan is to use external drives for storage of the shared files. One step at a time.

---

### Post by Morbius1 on 2021-10-22
The [homes] section of smb.conf is a special share in that it will create a samba share of a user's home directory on the fly for every local user on your Linux server. You will note that the [homes] share has no path. Otherwise the admin would have to create a share for user bob pointing to his home directory and another for alice for her home directory .... So you cannot turn it into MyFolder and expect to have the same result.

The valid user = %S is a convoluted way to say how the client user is expected to access the share. By default it is not set browseable and the user is expected not to access the share as //hostname/homes but as //hostname/$USER - as in //hostname/morbius for example. This Windows does by default. In Linux you have to specify it.

---

### Post by fjl05 on 2021-10-22
> **Morbius1 said:**
> Your calculation is correct but you are using the wrong base. 1+1 should equal 1.wouldn't that = 10 in binary?


> **Morbius1 said:**
> 
A "create mask" is converted to binary and then a logical AND is performed on the original permissions passed.
Yeah, but why?

---

### Post by Morbius1 on 2021-10-22
I'm done here.

Bone for tuna.

---

### Post by fjl05 on 2021-10-22
> **Morbius1 said:**
> The [homes] section of smb.conf is a special share in that it will create a samba share of a user's home directory on the fly for every local user on your Linux server. You will note that the [homes] share has no path. Otherwise the admin would have to create a share for user bob pointing to his home directory and another for alice for her home directory .... So you cannot turn it into MyFolder and expect to have the same result.

Thats fine but it works under this setting

```
[homes]
  comment = %Us Home Directory
  browseable = yes
  guest ok = no
  writable = yes

[Mario]
comment = Mario's Folder
path = /Users/U% 
browseable - no
valid users = Mario, Toad, Yoshi
```

If I login with Mario it uses the above [Mario] service along with its parameters. Basically the way I was expecting '**copy =**' to work. How does it know to use that service? If I change the name of the [Mario] service, then it defaults to the users home directory of /home/mario instead of the directory I set on [Mario] '**path=**'

Just trying to understand how its doing this.


> **Morbius1 said:**
> The valid user = %S is a convoluted way to say how the client user is expected to access the share. By default it is not set browseable and the user is expected not to access the share as //hostname/homes but as //hostname/$USER - as in //hostname/morbius for example. This Windows does by default. In Linux you have to specify it.
Not gonna lie, but I think I somewhat understand your explanation here.




> **Morbius1 said:**
> I'm done here.

Bone for tuna.

Thanks for you help.

---

### Post by TheFu on 2021-10-23
In many parts of Linux, the only real way to truly understand what is happening is to read the source code. Perhaps spend a few hours in a debugger watching it work.
For people who cannot do that, there are manpages and books written on specific topics.  O'Reilly has a book on Samba. I don't have it and never needed it.  Long ago, I learned what worked for my needs and have been using those settings all this time. When new stuff happens, I ask Mr. Scroogle for an answer, update my smb.conf until it does what I need.

I'm fairly security conscious.  Samba historically has been terrible at security until about 2 yrs ago, so I've always used the host allow/deny parts.  For about 10 yrs, I've drastically reduced my need for samba and most files on the network here are accessed using NFS or rsync or sftp or sshfs or ...  or ... or ... anything else.  My remaining Windows machines are basically stand alone and only get powered on 4x a month for some financial programs.  I also have multiple subnets and do not want anything from my lab "getting out" onto other parts of the LAN here. I definitely don't want and IoT or wifi stuff having access to Samba. That's just too crazy to consider, for me.

Samba is a complicated beast.  It is trying to make 1 OS appear as another when they have fundamental differences at the way files are handled.  The best non-book information that I know about samba settings is the smb.conf manpage.  Because it is long and complex, there are many parts that refer to other parts and all the tidbits for 1 settings aren't necessarily just in that page of the manpage.  There are many caveats spread throughout the manpage for many settings.  Not all settings can be used anywhere, for example. Some can only be used in the [global] stanza and others can only be used in a [share] stanza.  Mixing those up is a common issue.

Plus, samba can be an NT4 Domain controller, which added a bunch of other rules. I've completely avoided knowing anything about that. If I want an LDAP domain, I'll run openLDAP or 386Directory Server, not Samba. But a bunch of Windows people confuse Domain Controllers with other services which are completely separate on Unix-Like OSes.  Anyways, this stuff doesn't really apply to home users much ... unless they are MSFT-admin trained.

I've shown a stanza that works exactly as expected honoring the masks.  You didn't seem to follow that example, so I don't know what is different.  Some settings override others. Perhaps the order of my settings and being in the same stanza AND my global settings are what make it all work.  And in your situation, any one of those can break it.  **testparm -s** is the best way to share exactly what your system says, but I'm not expert enough (or have the pay) to look at everything. Sorry. I just know what works here.

If you have something working. Make a backup of those files, so you can always go back.  Then screw around as much as you like.

---

### Post by fjl05 on 2021-10-23
> **TheFu said:**
> In many parts of Linux, the only real way to truly understand what is happening is to read the source code. Perhaps spend a few hours in a debugger watching it work.
For people who cannot do that, there are manpages and books written on specific topics.  O'Reilly has a book on Samba. I don't have it and never needed it.  Long ago, I learned what worked for my needs and have been using those settings all this time. When new stuff happens, I ask Mr. Scroogle for an answer, update my smb.conf until it does what I need.

Yeah I suppose I can't expect to learn every little thing. As long as I have the settings I need and make notes of them it should be perhaps enough. Who's Mr. Scroogle?

> I'm fairly security conscious.  Samba historically has been terrible at security until about 2 yrs ago, so I've always used the host allow/deny parts.  For about 10 yrs, I've drastically reduced my need for samba and most files on the network here are accessed using NFS or rsync or sftp or sshfs or ...  or ... or ... anything else.  My remaining Windows machines are basically stand alone and only get powered on 4x a month for some financial programs.
Is samba even safe to use? I dont really plan to use it for anything but my LAN so I can store and access files. But say I wanted to access from the internet, would using Sambe be a security issue?  Really I wanted to try out Samba for the learning experience. But I've heard of openmedia vault. Would that be a better choice?


> I also have multiple subnets and do not want anything from my lab "getting out" onto other parts of the LAN here. I definitely don't want and IoT or wifi stuff having access to Samba. That's just too crazy to consider, for me.
Subnets is something else I need to look into implementing. There are things I need to separate. But again, one thing at a time. Networking is not an easy subject. Although learning it is definitely fun.

> Samba is a complicated beast.  It is trying to make 1 OS appear as another when they have fundamental differences at the way files are handled.  The best non-book information that I know about samba settings is the smb.conf manpage.  Because it is long and complex, there are many parts that refer to other parts and all the tidbits for 1 settings aren't necessarily just in that page of the manpage.  There are many caveats spread throughout the manpage for many settings.  Not all settings can be used anywhere, for example. Some can only be used in the [global] stanza and others can only be used in a [share] stanza.  Mixing those up is a common issue.
Manpage? got a link?

> Plus, samba can be an NT4 Domain controller, which added a bunch of other rules. I've completely avoided knowing anything about that. If I want an LDAP domain, I'll run openLDAP or 386Directory Server, not Samba. But a bunch of Windows people confuse Domain Controllers with other services which are completely separate on Unix-Like OSes.  Anyways, this stuff doesn't really apply to home users much ... unless they are MSFT-admin trained.
You just went over my head, buddy lol.

> I've shown a stanza that works exactly as expected honoring the masks.  You didn't seem to follow that example, so I don't know what is different.  Some settings override others. Perhaps the order of my settings and being in the same stanza AND my global settings are what make it all work.  And in your situation, any one of those can break it.  **testparm -s** is the best way to share exactly what your system says, but I'm not expert enough (or have the pay) to look at everything. Sorry. I just know what works here.

If you have something working. Make a backup of those files, so you can always go back.  Then screw around as much as you like.
Thats exactly what I'm doing. I find this kind of stuff tedious, yet its completely entertaining and fun. For me anyways. Thx for you help btw.

---

### Post by TheFu on 2021-10-23
> **fjl05 said:**
> Yeah I suppose I can't expect to learn every little thing. As long as I have the settings I need and make notes of them it should be perhaps enough. Who's Mr. Scroogle?

scroogle was a web search engine that didn't pass on any information to the upstream search engine.

> **fjl05 said:**
> 
Is samba even safe to use? I dont really plan to use it for anything but my LAN so I can store and access files. But say I wanted to access from the internet, would using Sambe be a security issue?  Really I wanted to try out Samba for the learning experience. But I've heard of openmedia vault. Would that be a better choice?
No networked service is "safe", but we can mitigate as many risks as possible.  Hence, why the deny/allow.
No way, no how, should you use CIFS/Samba over the internet!!!!  !!!!! !!!!!!!!!!  !!!!!!!!!!!
Use something based on ssh or through a full VPN that you host yourself.  sftp, scp, rsync, sshfs are all based on ssh.  sftp is built-into most Linux file managers.  Just use sftp://IP-address/ to access the resource you want. The firewall port for ssh needs to allow inbound connections. To mitigate attacks, use a non-standard port (never port 22/tcp), ssh-keys (NEVER, EVER, passwords), and run an automatic firewall blocker like fail2ban or denyhosts.  I still see brute force attempts on my systems, but just moving off the default port reduced the attempts 10,000x.

> **fjl05 said:**
> 
Subnets is something else I need to look into implementing. There are things I need to separate. But again, one thing at a time. Networking is not an easy subject. Although learning it is definitely fun.
It is very worthwhile to learn enough to handle subnetting in a home environment. You'll want a real router to handle that or a LAN router to be paired with your WAN router.  The router from the ISP is **not** to be trusted.

> **fjl05 said:**
> Manpage? got a link?
That's sorta funny.  My icon talks about xman.  **man man** at a shell prompt will explain manpages. Every Unix system since 1970 has manpages.

> **fjl05 said:**
> Thats exactly what I'm doing. I find this kind of stuff tedious, yet its completely entertaining and fun. For me anyways. Thx for you help btw.
There's always more to know.  I figure I know about 10% after 25+ yrs.

---

### Post by fjl05 on 2021-10-24
> **TheFu said:**
> scroogle was a web search engine that didn't pass on any information to the upstream search engine.


No networked service is "safe", but we can mitigate as many risks as possible.  Hence, why the deny/allow.
No way, no how, should you use CIFS/Samba over the internet!!!!  !!!!! !!!!!!!!!!  !!!!!!!!!!!
Why exactly not? Wouldn't later version be made to deal with the latest security issues? or is SAMBA made with the intention of being used as a file server only within a LAN setting?


> Use something based on ssh or through a full VPN that you host yourself.  sftp, scp, rsync, sshfs are all based on ssh.  sftp is built-into most Linux file managers.
Currently I use a VPN option built into my Asus router to connect to my LAN. It's openVPN. Is that safe?

> Just use sftp://IP-address/ to access the resource you want. The firewall port for ssh needs to allow inbound connections. To mitigate attacks, use a non-standard port (never port 22/tcp), ssh-keys (NEVER, EVER, passwords), and run an automatic firewall blocker like fail2ban or denyhosts.  I still see brute force attempts on my systems, but just moving off the default port reduced the attempts 10,000x.
SSH keys is something I also need to look into.


> It is very worthwhile to learn enough to handle subnetting in a home environment. You'll want a real router to handle that or a LAN router to be paired with your WAN router.  The router from the ISP is **not** to be trusted. The only thing I have from my ISP is the wire coming into my house. The modem is one I bought, and the router is also one I bought. ASUS RT-ACRH17


> That's sorta funny.  My icon talks about xman.  **man man** at a shell prompt will explain manpages. Every Unix system since 1970 has manpages. I didnt know this one, thanks. Still pretty new to Linux.


> There's always more to know.  I figure I know about 10% after 25+ yrs. only 10% :O

---

### Post by TheFu on 2021-10-24
> **fjl05 said:**
> Why exactly not? Wouldn't later version be made to deal with the latest security issues? or is SAMBA made with the intention of being used as a file server only within a LAN setting?

You have some understanding to gain, it seems.

> **fjl05 said:**
> Currently I use a VPN option built into my Asus router to connect to my LAN. It's openVPN. Is that safe?

Assume nothing is safe until YOU do the research on it.  If your router hasn't been patched this month, I'd assume there are known bugs being attacked now.  I don't know any consumer router that doesn't have a history of security failures.  Asus was so bad they are in a 20 yr agreement with the FTC for security issues.
In general, I think no WAN router should be used for anything but the core purposes.  That's routing and firewalling.  If you want a VPN, setup a VPN on a separate system that can be patched and maintained.  Any whatever you do, please don't think that a router is a NAS.

> **fjl05 said:**
> SSH keys is something I also need to look into.

This should be your first task. Before everything else.  ssh is how system communicate.  ssh-keys are 1,000,000x more secure than any password a human can enter.  ssh-keys are much more convenient that typing a password too.  How often is something both vastly more secure AND more convenient?  ssh, scp, sftp, rsync, sshfs, and most Unix backup tools are build using libssh ... which means those keys are automatically used for all those connections, once setup.  I've posted detailed instructions multiple times in these forums.

> **fjl05 said:**
>  The only thing I have from my ISP is the wire coming into my house. The modem is one I bought, and the router is also one I bought. ASUS RT-ACRH17
  Asus ... eh.

> **fjl05 said:**
>  I didnt know this one, thanks. Still pretty new to Linux.


> **fjl05 said:**
>  only 10% :O
Some days, I think only 1%. My systems humble me way too often.

---

### Post by fjl05 on 2021-10-24
> **TheFu said:**
> You have some understanding to gain, it seems.


Assume nothing is safe until YOU do the research on it.  If your router hasn't been patched this month, I'd assume there are known bugs being attacked now.  I don't know any consumer router that doesn't have a history of security failures.  Asus was so bad they are in a 20 yr agreement with the FTC for security issues.
In general, I think no WAN router should be used for anything but the core purposes.  That's routing and firewalling.  If you want a VPN, setup a VPN on a separate system that can be patched and maintained.How would I go about this exactly? like a vpn running on ubuntu? Would a raspberry pi work? also, wouldn't the machine running it require two ethernet ports?


> And whatever you do, please don't think that a router is a NAS.
Actually thats what I have now due to limitations. But not exactly what you think. I have a separate router which has NAS capability that I use to store all the videos from my IP cameras. This is not the router that acts as the WAN. This one is set as a DHCP client for its NAS capabilities which I plan to replace with the RasPi. Which is part of why I am learning all of this.


> This should be your first task. Before everything else.  ssh is how system communicate.  ssh-keys are 1,000,000x more secure than any password a human can enter.  ssh-keys are much more convenient that typing a password too.  How often is something both vastly more secure AND more convenient?  ssh, scp, sftp, rsync, sshfs, and most Unix backup tools are build using libssh ... which means those keys are automatically used for all those connections, once setup.  I've posted detailed instructions multiple times in these forums.yeah I'll make sure to look into it.

---

### Post by TheFu on 2021-10-24
> **fjl05 said:**
> How would I go about this exactly? like a vpn running on ubuntu? Would a raspberry pi work? also, wouldn't the machine running it require two ethernet ports?

Part of the skills important to being successful with Linux is where to search, how to search, and who to trust.
You are asking great questions, but the answers are only 10% of the problem. Skipping all the other things that need to be known and mastered would be a disservice. 

Here's a hint for where to look for ubuntu stuff ... look for websites with "ubuntu" in the domain part of the DNS name.
Providing "what" to type is 1000x less important than "why" - and the why aspects are critical, as are the "why not".  Just because we can do something, that doesn't make it a good idea and definitely doesn't make it secure.

When I was learning many of these things, Altavista was the main websearch engine. Everyone had bookmarks to remember where stuff was.  I stopped using bookmarks over a decade ago. The world has changed.

---

### Post by rsteinmetz70112 on 2021-10-27
> **Morbius1 said:**
> The [homes] section of smb.conf is a special share in that it will create a samba share of a user's home directory on the fly for every local user on your Linux server.** You will note that the [homes] share has no path.** 

It is possible to put a path statement into [homes] to define another location. On some of my machines I redirect the [homes] to another server and it works just fine. The default is path=/home/%U You could use that to have a separate home directory for Windows users.

---

### Post by TheFu on 2021-10-27
> **rsteinmetz70112 said:**
> It is possible to put a path statement into [homes] to define another location. On some of my machines I redirect the [homes] to another server and it works just fine. The default is path=/home/%U You could use that to have a separate home directory for Windows users.

I cannot see this method always working. The location of the HOME is determined by the getpwent() call.  It is NOT hard-coded to /home/{username}.  Just because something undocumented works, that doesn't mean it will forever.  But if it does work, great.

This is a key reason why the entire snap subsystem is broken.  The hard-coded /home rather than using the system records for each user.

---

### Post by rsteinmetz70112 on 2021-10-27
> **TheFu said:**
> I cannot see this method always working. The location of the HOME is determined by the getpwent() call.  It is NOT hard-coded to /home/{username}.  Just because something undocumented works, that doesn't mean it will forever.  But if it does work, great.

This is a key reason why the entire snap subsystem is broken.  The hard-coded /home rather than using the system records for each user.

The use of path={directory name} in a [homes] share is documented in the Samba documentation, although detail is sparse, but I assume the Samba Team has worked out how it should work. 

I took a little bit of a shortcut in my earlier post, skipping overs some stuff not usually needed. A normal users home is traditionally set in /etc/passwd and usually defaults /home/{username}, although root's home directory is generally set nowadays to /root and many special users have other home directories. If you use another method of authentication like ldap then it can be set there. You obviously know this. 

The samba backends handle Samba and Windows authentication so they also contain the home directory information and Windows User and Group information. Users can have different Linux and Samba passwords and home directories, among other things. Samba generally prepends the logon server name to the user home directory when you have a domain, showing \\SERVER\{homes path}\{username] wherever the user logins. Samba looks up the User Home Directory and if it can't finds one creates one. If you set the home directory to another server then the backend shows the Home directory server. There doesn't seem to be anything keeping Samba from doing a conditional check and if path={some random path} is set for [homes] using that. I can see some good reasons for having separate windows and Linux home share, I can also see complications. In our case only a few users use Linux directly so most users won't run into problems.

---

### Post by fjl05 on 2021-10-31
> **rsteinmetz70112 said:**
> It is possible to put a path statement into [homes] to define another location. On some of my machines I redirect the [homes] to another server and it works just fine. The default is path=/home/%U You could use that to have a separate home directory for Windows users.

But how would I be able to add different parameters for each user that logs in?

---

### Post by TheFu on 2021-10-31
> **fjl05 said:**
> But how would I be able to add different parameters for each user that logs in?

Use NFS.  Then POSIX permissions work.

---

### Post by fjl05 on 2021-11-02
Isn't NFS linux only? I'm sharing with Windows stations.
Will using NFS require relearning a whole new program? Took me a good while to get a hang of Samba, lol.

---

### Post by TheFu on 2021-11-03
NFS is a hassle from Windows clients. I haven't used it since the 1990s and it was always a 3rd party tool on Windows.  I think MSFT added it for Pro/Enterprise/Ultimate Windows desktops, but buried it in some uninstalled options.  A few people in these forums have set it up. Just not me.  

I attempted NFS as a client on a Win7 Ultimate virtual machine setup, but never got it working. I didn't try too hard, as it wasn't on a system that really needed it. I prefer NFS since it honors Unix-native file ownership, groups, permissions, xattrs and ACLs, unlike Samba.  But each of us have different levels of "hassle" with which we are willing to put up. 

[https://smallbusiness.chron.com/connect-windows-client-nfs-server-50773.html](https://smallbusiness.chron.com/connect-windows-client-nfs-server-50773.html) makes it seem easy.
[https://ostoday.org/linux/how-do-i-access-nfs-share-from-windows-10-to-linux.html](https://ostoday.org/linux/how-do-i-access-nfs-share-from-windows-10-to-linux.html) is another guide.

---

### Post by fjl05 on 2021-11-11
How does Samba not honor file ownership and permissions? It seems to do so on all the testing I've done.

---

### Post by TheFu on 2021-11-11
> **fjl05 said:**
> How does Samba not honor file ownership and permissions? It seems to do so on all the testing I've done.


sudo chown
chmod
chgrp

Try any of those over samba/cifs mounted storage and see that they don't work.  If you are mainly Windows-user, you'd likely never notice.  If you actually "use" permissions in a mixed way like teams do, it will be painful.

---

### Post by fjl05 on 2021-11-18
> **TheFu said:**
> sudo chown
chmod
chgrp

Try any of those over samba/cifs mounted storage and see that they don't work.  If you are mainly Windows-user, you'd likely never notice.  If you actually "use" permissions in a mixed way like teams do, it will be painful.

I found that to be true when mounting NTFS, exFAT or FAT32 drives which in my testing had nothing to do with samba but instead with the mounted drives themselves. But if I stick to EXT4 I end up having no problems using the commands you mentioned on mounted drives. So I'll be sure to only be using EXT4 partitions for file sharing drives.

---

### Post by TheFu on 2021-11-18
> **fjl05 said:**
> I found that to be true when mounting NTFS, exFAT or FAT32 drives which in my testing had nothing to do with samba but instead with the mounted drives themselves. But if I stick to EXT4 I end up having no problems using the commands you mentioned on mounted drives. So I'll be sure to only be using EXT4 partitions for file sharing drives.

Sorry I wasn't clear.

If you mount any storage over CIFS/SAMBA, then those commands do not work THRU THE MOUNT from the client machine to the shared storage.  The protocol doesn't support it. This is one reason why using NFS rather than CIFS/Samba between Unix systems that share storage over the LAN is useful. There are others.

If you access the underlying storage while logged into the server sharing the CIFS/SAMBA network mounts, then only native Linux/Posix storage will support those commands, as you've seen.

---

