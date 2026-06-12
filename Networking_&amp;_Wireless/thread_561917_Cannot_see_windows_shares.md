---
title: "Cannot see windows shares"
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by FarmerJo on 2007-09-28
Hi,

I have ubuntu FF installed on one PC and another PC with windose xp on it that has a number of shares. When I run Nautilius from the ubuntu machine and select Browse Network an icon is displayed for the windose pc but when I click on it I cannot see any of its shares. 

Do I need any additional configuration for this to work?
Also what would be the settings required in the Connect to Server page to establish a connection to the PC (i) as an administrator and (ii) to a share?

The windows PC settings are as follows.

Workgroup: WIN_WG
User: Admin
Password: any_pw
Share: Audio

Any help would be appreciated.

FarmerJo

---

### Post by bigken on 2007-09-28
try this in a treminal

sudo apt-get install samba
sudo smbpasswd -a yourname
sudo smbpasswd -e yourname

---

### Post by FarmerJo on 2007-09-28
I ran these commands but still ended up getting the message "The folder could not be displayed". Windows network appears and within this the workgroup appears. Cannot seem to get into the workgroup to see the shares.

When I executed the first command it did appear to indicate some error messages part way through its execution. Also I am assuming that yourname means the user name used to log into ubuntu. When the second command was executed the password I entered was the one I use to log into ubuntu. Is this right so far?

Regards
FarmerJo

---

### Post by FarmerJo on 2007-09-28
Just a thought.

I know for a windozy system in order to see the shares of another machine both machines need to have the same workgroup. How do I check the workgroup that I am in for the ubuntu system?

Also could someone tell me what the three sudo commands do in the previous post?

Regards
FarmerJo

---

### Post by bigken on 2007-09-28
-a adds user 
-e enables user 

yes your its your login name 

have you rebooted the pc ?

---

### Post by FarmerJo on 2007-09-28
Did a reboot but still no success yet. 

Regarding these three sudo commands again. Do these need to be executed for every new installation of ubuntu?

When I click the Windows Network icon there are two items within it. One is the workgroup of the windows PC that I am trying to access the shares of and the other is mshome. 

If I click into mshome it shows a single file named UBUNTU-DESKTOP which presumably is the desktop for my login. When I click on this I see no files even though my desktop does have some directories on it. Does this mean that there are two separate workgroups on the network, one for the windose pc and the other for the ubuntu pc?

Regards
FarmerJo

---

### Post by bigken on 2007-09-28
on your windows pc run the network wizard and used mshome as your network 

on your ubuntu pc go to system/preferences shared folders and add your home directory

---

### Post by FarmerJo on 2007-09-28
Did that and the windose pc can see the ubuntu pc but still not the other way around. I have even disabled the windose pc firewalls.

---

### Post by bigken on 2007-09-28
is this xp or vista

also have you shared any files on windows pc ?

---

### Post by FarmerJo on 2007-09-28
xp sp2!

---

### Post by FarmerJo on 2007-09-28
Lots of shares too!

---

### Post by bigken on 2007-09-28
ok try this in a terminal 



sudo /etc/init.d/samba restart


I would also try running your win xp shares again as theres were setup in workgroup not mshome

---

### Post by FarmerJo on 2007-09-28
Did as you said but still no joy yet. We'll get there soon I'm sure of it!

---

### Post by bigken on 2007-09-28
rerun the windows shares 

and reboot both pc's

---

### Post by FarmerJo on 2007-09-28
Got a bit further this time - many thanks.

I can not see the windows PC from ubuntu but cannot access its shares from within it.

---

### Post by bigken on 2007-09-28
i would rerun win xp network wizard again 

also how many firewalls do you have ?

in your windows my network places remove all your shares and the add them again

---

### Post by FarmerJo on 2007-09-28
I have Norton 360 and have disabled its firewall. Also the windows firewall is disabled. I have rerun network identification and reestablished the workgroup as MSHOME.

Also created a new share on the windows pc with a few junk files in it.

Restarted the windows pc but still no joy. I seem to remember having similar problems to these when I first got the windows network to run.

FarmerJo

---

### Post by FarmerJo on 2007-09-28
Off to the fair now but I will still be thinking this one through. Thanks for all your help it is much appreciated. Hope to communicate soon.

What does the number of beans that you have against your username mean?

Regards
FarmerJo

---

### Post by bigken on 2007-09-28
did you also turn the windows firewall off 

the beans are just for fun do a search on them in the forum 

anyhow have fun im off to the pub soon too lol hic :p

---

### Post by FarmerJo on 2007-09-30
Yes the windows firewall is off.

I thought I would run through the three samba commands again this morning but now I am having problems with the this one.

sudo smbpasswd -a yourname

First I type in my account password then when prompted the same again another twice. I am now getting this error.

"Failed to modify password entry for user yourname"

Any ideas why this is happening?

Do I need to run these commands every time I start the ubuntu machine?

Regards
FarmerJo

---

### Post by calexbg on 2007-10-01
i had that problem too.. when it says <yourname> it means whatever the ubuntu login is that you are currently logged into.  if you enter anyhting else it doesnt work.  this might mean that you need to log into each of your users' accounts and  run   

sudo smbpasswd -a <user> for each user and then 
sudo smbpasswd -e <user>   


i might be wrong but that is how it worked out for me.   I am also suffering from a similar networking issue.  my windows xp and edubuntu computers cannont see eachother, but i can see other windows computers that are on the same local network as both computers

---

### Post by moschops on 2007-10-21
I'm having the exact same problem as FarmerJo - I just did a fresh install of Gutsy Gibon RC 1 on a machine that previously was able to browse my Windows network with no problems.  I've done the usual setting of the workgroup in smb.conf and I am able to Places->Connect to Server and put in the Windows machine by IP address to browse a share, but when I go browse the network I only see WORKGROUP (my workgroup name) plus the local Ubuntu machine name listed.  No other windows machines appear to be listed.  

I've done all the smbpasswd stuff and my Ubuntu user name and password match that what I have on my Windows machines... like I said with Feisty this was working fine but now it is busted.

Plus I cannot ping my Windows machines by their WINS host name - but I can by IP address.

---

