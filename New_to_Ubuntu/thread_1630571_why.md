---
title: "why?"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by Jackal913 on 2010-11-25
ok this is not my first dance with Linux, I am having 2 problems with linux one I am running Ubutu Ultimate 2.8 at the moment and this time around it did not ask me for a root password and I can not do anything as root ie the last time you log out and log in as root pass root it does not work everything is asking me for a password and if i bring up the terminal and type man root it replies no entry, if I use sudo it tells me i'm not in the sudo list.... or not logged in as root????

second problem I have a few programs that require sun java to run and if you go to the sun web sight to down load it, it comes down as a .bin if it were a .deb file i wouldn't be addressing it, I have tried for days to install the jre.bin file and I get nowhere

why if this OS is such a super OS does it still have bash commands in stead of just installing it's not a wonder why linux is not used more, it's because you don't have these problems with windows, why can't someone write a universal extract install program or script or use a universal program, it's just mind 
boggling i'm not a stupid person and if I have to learn mundane bash commands I will get used to it, but if we are so technological why can't we come up with a simpler solution to such a complex problem???? that's all i'm saying, im sure if it was simpler there would be more people switching

---

### Post by madjr on 2010-11-25
> **Jackal913 said:**
> ok this is not my first dance with Linux, I am having 2 problems with linux one I am running Ubutu Ultimate 2.8 at the moment and this time around it did not ask me for a root password and I can not do anything as root ie the last time you log out and log in as root pass root it does not work everything is asking me for a password and if i bring up the terminal and type man root it replies no entry, if I use sudo it tells me i'm not in the sudo list.... or not logged in as root????

second problem I have a few programs that require sun java to run and if you go to the sun web sight to down load it, it comes down as a .bin if it were a .deb file i wouldn't be addressing it, I have tried for days to install the jre.bin file and I get nowhere

why if this OS is such a super OS does it still have bash commands in stead of just installing it's not a wonder why linux is not used more, it's because you don't have these problems with windows, why can't someone write a universal extract install program or script or use a universal program, it's just mind 
boggling i'm not a stupid person and if I have to learn mundane bash commands I will get used to it, but if we are so technological why can't we come up with a simpler solution to such a complex problem???? that's all i'm saying, im sure if it was simpler there would be more people switching

first, welcome to the forums

"ultimate" is not an official ubuntu release. In fact it cant use the name "Ubuntu" because of this.

We dont know what they've taken out or what they added.

---

### Post by nlsthzn on 2010-11-25
In a nutshell, Linux != Windows...

---

### Post by Jackal913 on 2010-11-25
ok so .bin is a universal problem how do I solve it?

---

### Post by madjr on 2010-11-25
> **nlsthzn said:**
> In a nutshell, Linux != Windows...

actually i dont think thats the issue

the problem is that ubuntu has the software center to install apps easily, but clearly hes not using it.

I dont know if this "ultimate" has it or not...

---

### Post by howefield on 2010-11-25
For your sudo problem, you might try the Ultimate forums..

[http://forumubuntusoftware.info/](http://forumubuntusoftware.info/)

and you might try this tutorial for the Java issue, which gives you 2 ways to install including the easy one via the repository.

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by madjr on 2010-11-25
> **Jackal913 said:**
> ok so .bin is a universal problem how do I solve it?

if things fail, you can install java very easily in normal ubuntu, using the software center or by installing restricted-extras. Check if your distro has one.

Also, i know linuxmint comes with java already preinstalled

but yea, you may want to try first on their forums and ask them if they changed anything.

---

### Post by tarps87 on 2010-11-25
(Based on an official Ubuntu release)

The first user you create will have su powers unless you have disabled them, root is disabled in Ubuntu hence the reliance on sudo.

To install java 
```
sudo apt-get install sun-java6-jre
```
or search in applications -> add/remove

Note: As stated above this is based on an official release, any issues you have with Ultimate edition should be addresed here
[http://forumubuntusoftware.info/](http://forumubuntusoftware.info/)

---

### Post by t4thfavor on 2010-11-25
Boot into safemode/recovery by pressing esc on the GRUB menu and selecting the recovery kernel (or single user) if it hasn't been disabled, it should let you passwd root, and then you can be on your way.

Again, this is not official Ubuntu, so it may be much different than what were all used to working with here.

---

### Post by Jackal913 on 2010-11-25
> **madjr said:**
> actually i dont think thats the issue

the problem is that ubuntu has the software center to install apps easily, but clearly hes not using it.

I dont know if this "ultimate" has it or not...

I used Ubuntu software center Ultimate has it at the bottom of the Applications menu, it say it is installed, but if you go to the sun java site and test to see if it is, it says it is not, infact if I do happen to download a .deb file ie Clementine which is a way better music program than Amorak will ever be, and I click it Ubuntu software center installs it, that's great i love it, it's the other stuff i.e., .bin, .tar.gz i know they are different and i'm sure that seasoned linux users don't have problems installing such files I do, and untill I become seasoned I will, sorry

---

### Post by Jackal913 on 2010-11-25
> **tarps87 said:**
> (Based on an official Ubuntu release)

The first user you create will have su powers unless you have disabled them, root is disabled in Ubuntu hence the reliance on sudo.

To install java 
```
sudo apt-get install sun-java6-jre
```
or search in applications -> add/remove

Note: As stated above this is based on an official release, any issues you have with Ultimate edition should be addresed here
[http://forumubuntusoftware.info/](http://forumubuntusoftware.info/)

russ@russ-ubuntu:~$ sudo apt-get install sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jre' has no installation candidate
russ@russ-ubuntu:~$ 

for someone not being allowed to use ubuntu's name because it's not an "official ubuntu relesae" it sure is poping up everyware LOL just saying

---

### Post by QLee on 2010-11-25
Yes, welcome to the forum. Interesting nick you've chosen.

I certainly "hear" your frustration and frustration usually makes troubleshooting more difficult.

[QUOTE=Jackal913]ok this is not my first dance with Linux, I am having 2 problems with linux one I am running Ubutu Ultimate 2.8 at the moment ...[/QUOTE]

As was mentioned by madjr, not an Ubuntu release, probably that's the reason for you becoming confused and getting to the wrong forum, thinking it was Ubuntu.

[QUOTE=Jackal913]second problem I have a few programs that require sun java to run and if you go to the sun web sight to down load it, it comes down as a .bin if it were a .deb file i wouldn't be addressing it, I have tried for days to install the jre.bin file and I get nowhere[/QUOTE]

However, this isn't an Ubuntu problem either, I can't think of a reason that would compel Sun to necessarily include a Debian package manager file since it isn't only Debian and derivatives that use Sun Java. In Ubuntu we can install Java from the Ubuntu repositories.

[QUOTE=Jackal913]why if this OS is such a super OS does it still have bash commands in stead of just installing it's not a wonder why linux is not used more, it's because you don't have these problems with windows, [/QUOTE]
Well, you'll now know that OS isn't Ubuntu. 

Your opinion is different than mine, I consider using the command line advanced, not something to be done away with.

[QUOTE=Jackal913]why can't someone write a universal extract install program or script or use a universal program, it's just mind boggling i'm not a stupid person and if I have to learn mundane bash commands I will get used to it, but if we are so technological why can't we come up with a simpler solution to such a complex problem???? [/QUOTE]

Well, since GNU/Linux distributions vary fairly widely, there are very few developers who have the necessary experience with the different distros to do something like that, think of the time it would take to be familiar with them all and most of these people are volunteers and have to earn a living somewhere. But, gosh, you can't load Win 3.0 drivers on XP or many XP applications on Vista or 7, can you ...or 95, or 98, or ME. I also wonder why you can't use a carb. from a 1970 Pontiac on a 1970 Ford or on a fuel-injected 1988 Dodge but, that's the way it is.

[QUOTE=Jackal913]that's all i'm saying, im sure if it was simpler there would be more people switching[/QUOTE]

Well, not everyone's goal is to get people to switch, some want that, but personally I don't care, people should use what they can use and choose to use.

Why don't you try Ubuntu, there will be lots of users here in this forum who would be glad to try and help you with something we understand.

---

### Post by tarps87 on 2010-11-26
> **Jackal913 said:**
> russ@russ-ubuntu:~$ sudo apt-get install sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jre' has no installation candidate
russ@russ-ubuntu:~$ 

for someone not being allowed to use ubuntu's name because it's not an "official ubuntu relesae" it sure is poping up everyware LOL just saying

In that case you are not using the latest version or it is using a different software repository, I would suggest asking on the ultimate edition forum about this.
My personal suggestion would be to try the official Ubuntu release as you can install all the apps in ultimate edition on an normal release.

---

### Post by 3rdalbum on 2010-11-26
You need to enable the Partner repository first.

System > Administration > Synaptic Package Manager.

Settings > Repositories

Under the "Other Repositories" tab, check "Canonical Partners".

Close the window, you'll be prompted to reload the package list. Do this, close Synaptic, and then you can install sun-java6-jre (or you can do this within Synaptic).

As for your "root" issue, it sounds like you don't understand the differences between Ubuntu and Windows, and you've followed some advice somewhere that has turned out badly. On Ubuntu Forums we don't tell anyone how to enable the root account, basically because there's never a happy ending to this. You don't need a root account - you can just use 'sudo'.

---

### Post by oldos2er on 2010-11-26
> **Jackal913 said:**
> E: Package 'sun-java6-jre' has no installation candidate


Does Ultimate use Ubuntu's repositories? The Sun java packages are in the partner repository, which you'll need to enable.

Edit: I should read more carefully--beaten to it.

---

