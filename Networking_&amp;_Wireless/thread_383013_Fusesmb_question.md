---
title: "Fusesmb question"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by mjcoury on 2007-03-12
Hey all - 

looks like I am late to the party with Fusesmb integration.  I have it all set up via various tutorials on teh interweb and Thunar seems to have properly accepted everything since I have my "music" folder from my windows server showing up, but when I click on it it simply says that 

"Failed to open directory "Music".
Permission Denied 

I am assuming that is becuase I do not have the correct username/password to get into my server.... any ideas where that kind of info is stored?

Cheers - 


Mike

---

### Post by mjcoury on 2007-03-24
Anyone............ Bueler?

---

### Post by dolphin_oracle on 2007-03-24
in your home folder there is a hidden directory called /.smb .  In this folder SHOULD be a file called fusesmb.conf.  You'll need to do a "sudo su" then edit the file as root.  put the following in the file

[global]
username=YOURSHAREUSERNAME
password=YOURSHAREPASSWORD

you can also set up specific server and share setups in the same file.  You can do a 


info fusesmb.conf 


for more information as I've now told you all I know :)

---

