---
title: "help please trying to connect to windows shares"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by clone_tk422 on 2007-03-30
Hi all

Wondering if someone can please help

I cannot connect to my windows shares..

I am using Windows Vista Ultimate

Ubuntu 6.10

Ok I have installed Samba and I can successfully connect to ubuntu share on windows box but not vice versa

If I try to connect to my windows server, I get the authentication to enter username password.

Ok n my vista machine, I have a user setup with a password I have the share setup with permissions set to everything for the groups of anonymous users, guest, everyone etc so pretty much any group can access and read/write to the share

on file sharing in vista i have password sharing off

on my ubuntu i have set up a user and password and added them to samba but dont know if thats what the problem is as when i run the commands sudo sambapasswd etc i get no return prompt saying if successfull or not. I have added conf file passwords something in samba dir

basically when i try to connect to windows share I have tried every user name and password combo, but no go.

i have tried my windows user/pass in the format of username password and servername\username password. I have tried administrator and password, i have tried the username password i created with samba

basically nothing lets me in.. dont know what else to try. I cant access the same swat tool to check settings, how else can i check any config files or anything to make sure the samba users etc are setup properly??

thanks

---

### Post by AhrenBa on 2007-07-04
> **clone_tk422 said:**
> Hi all

Wondering if someone can please help

I cannot connect to my windows shares..

I am using Windows Vista Ultimate

Ubuntu 6.10

Ok I have installed Samba and I can successfully connect to ubuntu share on windows box but not vice versa

If I try to connect to my windows server, I get the authentication to enter username password.

Ok n my vista machine, I have a user setup with a password I have the share setup with permissions set to everything for the groups of anonymous users, guest, everyone etc so pretty much any group can access and read/write to the share

on file sharing in vista i have password sharing off

on my ubuntu i have set up a user and password and added them to samba but dont know if thats what the problem is as when i run the commands sudo sambapasswd etc i get no return prompt saying if successfull or not. I have added conf file passwords something in samba dir

basically when i try to connect to windows share I have tried every user name and password combo, but no go.

i have tried my windows user/pass in the format of username password and servername\username password. I have tried administrator and password, i have tried the username password i created with samba

basically nothing lets me in.. dont know what else to try. I cant access the same swat tool to check settings, how else can i check any config files or anything to make sure the samba users etc are setup properly??

thanks

I am having this exact same problem. Have you found a solution?

---

### Post by clone_tk422 on 2007-07-04
> **AhrenBa said:**
> I am having this exact same problem. Have you found a solution?

Hi, 

I'm not using Ubuntu anymore but I think I did manage to work it out. The only thing is I couldnt get it to work where it asks me for a user name and password as I the username and password never worked. I was able to get it working so I could connect to the shares anonymously and so I didnt need a user / password

This is fine for me as I'm only using the shares in my home so I dont need the protection of password protecting my shares so my solution will only be of use to you if you also dont care about needing a password to access shares.

Firstly go in and in the sharing properties make sure you allow ANONYMOUS_USER access to the share and if needed give it full permissions.. 

Normally this setting is enough for other windows PC's to connect to the share anonymously but wasnt working for Ubuntu

to fix this, i went into Control Panel / Administrative Tools / Local Security Settings / Local Policies and I think its the setting something like NETWORK ACCESS: Shares that can be accessed anonymously

In this setting I put all my share names in that I wanted to connect to and now I was able to connect to them through Ubuntu and it didnt even ask me for a user name / password

The other thing you want to check is when you go into sharing properties in vista, you set up permissions for the share but I found in Vista there is also a SECIRITY TAB and you also need to go in and set the permissions for this as well. So in my case i also allow anonymous access with full permissions in the security tab as well as the sharing tab.

Hope this helps

---

### Post by AhrenBa on 2007-07-04
> **clone_tk422 said:**
> Hi, 

I'm not using Ubuntu anymore but I think I did manage to work it out. The only thing is I couldnt get it to work where it asks me for a user name and password as I the username and password never worked. I was able to get it working so I could connect to the shares anonymously and so I didnt need a user / password

This is fine for me as I'm only using the shares in my home so I dont need the protection of password protecting my shares so my solution will only be of use to you if you also dont care about needing a password to access shares.

Firstly go in and in the sharing properties make sure you allow ANONYMOUS_USER access to the share and if needed give it full permissions.. 

Normally this setting is enough for other windows PC's to connect to the share anonymously but wasnt working for Ubuntu

to fix this, i went into Control Panel / Administrative Tools / Local Security Settings / Local Policies and I think its the setting something like NETWORK ACCESS: Shares that can be accessed anonymously

In this setting I put all my share names in that I wanted to connect to and now I was able to connect to them through Ubuntu and it didnt even ask me for a user name / password

The other thing you want to check is when you go into sharing properties in vista, you set up permissions for the share but I found in Vista there is also a SECIRITY TAB and you also need to go in and set the permissions for this as well. So in my case i also allow anonymous access with full permissions in the security tab as well as the sharing tab.

Hope this helps

Wow, thanks for the detailed response! I am afraid I cannot find many of the things you are explaining because I am on XP home. :( Do you have any ideas how this process would work in XP? Thanks a ton!

---

### Post by clone_tk422 on 2007-07-04
> **AhrenBa said:**
> Wow, thanks for the detailed response! I am afraid I cannot find many of the things you are explaining because I am on XP home. :( Do you have any ideas how this process would work in XP? Thanks a ton!

The part about Control Panel - Local Security Policy - Security Options and setting Network Access shares that can be access anonymously should be the same in XP home

Also XP Home should have the same TABS for Sharing and Security when you right click on the folder you want to share and select option Sharing

Just make sure in Permissions for the sharing tab you add the anonymous user and give them full control and in the security TAB hit add and also add anonymous user..

If they are not there Im not really sure about XP home as I have only used XP professional. 

Let me know how you get on and if I can help further.

---

### Post by scxtt on 2007-07-04
on ubuntu:

sudo smbpasswd -a $USER

then try your connections again ...

---

