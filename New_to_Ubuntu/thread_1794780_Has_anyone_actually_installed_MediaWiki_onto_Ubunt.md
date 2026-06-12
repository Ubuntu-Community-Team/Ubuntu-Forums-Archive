---
title: "Has anyone actually installed MediaWiki onto Ubuntu Server"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by edisonmax on 2011-07-01
Because I am trying desperately to do this. I thought it was simple, but its thus far proving not to be.

When i have asked on this forum i get several completely different answers.

I have learnt Linux Command which helped alot but i still feel like it was like learning about quantum mechanics so that i can drive a car. Im looking for a "need to know" basis. Its nice to know how things are organised etc but at the end of the day I dont care, especially when this has not achieved my goal.

So see if anyone can do the unthinkable and tell me what i have to do. My setup:

I have a Macbook Pro.
On this i have VMWare Fusion.
As a virtual machine i have installed ubuntu server

I have LAMP installed. I did this when i was installing ubuntu server. I clicked the option for LAMP.

Theres no GUI just the command line (so please dont say i need to click on an icon)

I have the Mediawiki file on a usb stick. Its been extracted on the same usb stick.

Now all i want to do is install mediawiki onto my ubuntu. Thats it. Thats all i am wanting to do. I didnt think it was much to ask.

So there it is. This is where i am.

Lets see if you can tell me what on earth I have to do. I am unable to find the usb stick through Moun or /mnt. It just aint happening.

***[I]_[SIZE="4"]I have tried everything, and I simply can not do it.[/SIZE]_*[/I]**

---

### Post by lisati on 2011-07-02
Yes, I have done it, but it was a while ago, and I can't remember exactly what I did to get it to work, possibly something to do with permissions and/or creating the required database through webmin.

---

### Post by alphacrucis2 on 2011-07-02
```
sudo apt-get install mediawiki
```

It's in the repos (v 1.15). Not sure if that will be the version you want as the latest is 1.17

---

### Post by Gryllida on 2011-07-02
I'm asking for more details.

Please open the Fusion Settings window. Select "USB Devices". Is your USB device listed there?

Thank you.

---

### Post by alphacrucis2 on 2011-07-02
As a matter of interest I installed mediawiki from the repos. It also recommended installing mediawiki-math, which I decided not to do as it pulls in texlive and a heap of other stuff of around 750mb. I guess you would really want all that if you want your wiki to support mathematical equations and the like. After installing it It wasn't quite sure what to do next but the ubuntu documention came to the rescue:

[https://help.ubuntu.com/community/MediaWiki](https://help.ubuntu.com/community/MediaWiki)

You have to uncomment a line in the apache config file and then restart apache. Then in your browser localhost/mediawiki and bingo. It walks you through the rest of the set up.

---

### Post by edisonmax on 2011-07-02
> **Gryllida said:**
> I'm asking for more details.

Please open the Fusion Settings window. Select "USB Devices". Is your USB device listed there?

Thank you.

Yes. and i have selected it. i have then gone to look fo it in /media and nothing cant see it.


this is the problem i have no-ones really done it or it was a long time ago etc.

i am going to have another go tonight on [https://help.ubuntu.com/community/MediaWiki](https://help.ubuntu.com/community/MediaWiki)

but im not hopeful.

I thought it would be easier and simpler to do it non-remotely but nope.

Also i dont know how to uncomment a line on the config apache file


im pretty sure ive done; "sudo apt-get install mediawiki" and its said it cant find mediawiki

---

### Post by Gryllida on 2011-07-02
You could try to mount the USB device manually in this case. [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by alphacrucis2 on 2011-07-03
> **edisonmax said:**
> Yes. and i have selected it. i have then gone to look fo it in /media and nothing cant see it.


this is the problem i have no-ones really done it or it was a long time ago etc.

i am going to have another go tonight on [https://help.ubuntu.com/community/MediaWiki](https://help.ubuntu.com/community/MediaWiki)

but im not hopeful.

I thought it would be easier and simpler to do it non-remotely but nope.

Also i dont know how to uncomment a line on the config apache file


im pretty sure ive done; "sudo apt-get install mediawiki" and its said it cant find mediawiki

You have to make sure the universe repo is enabled. 

If you don't know how to enable it post your /etc/apt/sources.list file back here for further insrtuction.


To edit the apache2 config file, the ubuntu mediawiki doc page tells you one of the ways to do that using the nano editor. Uncommenting the line means delete the # at the beginning of the line.


Once you get the repo issue sorted that will definitely be the easiest way if you are unfamiliar with the command line. I got the repo version of mediawiki up and running in less than ten minutes last night.

---

### Post by edisonmax on 2011-07-03
> **alphacrucis2 said:**
> You have to make sure the universe repo is enabled. 

If you don't know how to enable it post your /etc/apt/sources.list file back here for further insrtuction.


To edit the apache2 config file, the ubuntu mediawiki doc page tells you one of the ways to do that using the nano editor. Uncommenting the line means delete the # at the beginning of the line.


Once you get the repo issue sorted that will definitely be the easiest way if you are unfamiliar with the command line. I got the repo version of mediawiki up and running in less than ten minutes last night.

ok so what is the universe repo?? 
Also I have no idea what you mean when you say "post your /etc/apt/sources.list back here for further instructions" I have managed to get to etc/apt and i can see the contents but dont what to do or how to open sources.list

Again its all very unclear as to what i am doing or more importantly what i meant to do.

---

### Post by alphacrucis2 on 2011-07-03
> **edisonmax said:**
> ok so what is the universe repo?? 
Also I have no idea what you mean when you say "post your /etc/apt/sources.list back here for further instructions" I have managed to get to etc/apt and i can see the contents but dont what to do or how to open sources.list

Again its all very unclear as to what i am doing or more importantly what i meant to do.

On repositories read this:

[URL="https://help.ubuntu.com/community/Repositories/Ubuntu"]https://help.ubuntu.com/community/Repositories/Ubuntu
[/URL]

They are stores of prepackaged software from which you can selectively install in to your Ubuntu system over the internet using the package management system. Universe is the name of one of the stores. As the doc above says:

> Universe - Community maintained software, i.e. not officially supported software. 


Mediawiki has been packaged by some kind soul and loaded into the universe repository so anyone can easily install it.

As you are running the server version you need to enable universe through editing /etc/apt/sources.list which is a configuration file for the package management system. A simple way to list the contents of the file is:

```
cat /etc/apt/sources.list
```

If you post the contents back here we will be able to see what you currently have configured and advise what to do next.

---

### Post by edisonmax on 2011-07-08
alphacrucis2,

your input has been the best help Ive had so far, so thank you so much for that. Also the fact that you have actually installed Mediawiki in 10 minutes no less certainly makes you my new best friend.

I just need a little bit more help to reach my goal/dream.

When I type in;

```
cat /etc/apt/sources.list
```

this is what i get back:

```

## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted 
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted 
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the 
## rerespective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## Uncomment the following two lines to add software from Ubuntu's
##  'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu natty main 
# deb-src http://extras.ubuntu.com/ubuntu natty main

```

Now, it looks like part of the results has been cut off so im wondering is there something wrong with my  window, or is this the results in their entirety? when i try to enlarge the window the text enlarges with it.

Also i am unable to type "~" and also "#". So i am wandering whether i selected the correct keyboard configuration when i was installing ubuntu server?

---

### Post by alphacrucis2 on 2011-07-09
This is my sources.list from the laptop I installed mediawiki on. Ignore the Getdeb bit at the end. I added that to get some packages from getdeb. I also have several PPA's but they have their own *.list files under /etc/apt/sources.d

Anyway:

```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://archive.ubuntu.com/ubuntu natty main restricted universe multiverse

###### Ubuntu Update Repos
deb http://archive.ubuntu.com/ubuntu natty-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu natty-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu natty-proposed main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu natty-backports main restricted universe multiverse

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu natty partner

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### GetDeb - http://www.getdeb.net
## Run this command: wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
deb http://archive.getdeb.net/ubuntu natty-getdeb apps
```

As I say you don't need that bit following unofficial repos. Not sure why you are having trouble with ~ and # keys but could well be a wrong keyboard mapping as you say.

Then

```
sudo nano /etc/apt/sourcesnew.list
```

Copy the text above (excluding the part following "Unofficial repos" into the new file and then save and exit.

Then 

```
sudo mv /etc/apt/sources.list /etc/apt/sourcesold.list
sudo mv /etc/apt/sourcesnew.list /etc/apt/sources.list
```

The first command renames the exiting sources.list so we can get it back if something goes wrong. The second command renames the file created by nano above.
 

Then issue the following commands:

```
sudo apt-get update
```

That will bring your repo indexes into sync. Then:

```
sudo apt-get install mediawiki
```

You do the rest of the mediawiki setup as per the docs previously linked.

---

### Post by edisonmax on 2011-07-13
Ok did what you said. 

Got to this part:

```
sudo apt-get update
```

and it said "temporary failure resolving" fo each deb line.

It then got to this

```
sudo apt-get install mediawiki
```

It says that it can't find it.


N.B. The machine that is running on it is not actually connected to the internet. Could this be the cause of the problem?? I wouldnt know how you connect it to the internet in any case.

I intend on building it offline and then rent some server space for me to upload to.

So in short i have not got it up and running.

---

### Post by alphacrucis2 on 2011-07-14
> **edisonmax said:**
> Ok did what you said. 

Got to this part:

```
sudo apt-get update
```

and it said "temporary failure resolving" fo each deb line.

It then got to this

```
sudo apt-get install mediawiki
```

It says that it can't find it.


N.B. The machine that is running on it is not actually connected to the internet. Could this be the cause of the problem?? I wouldnt know how you connect it to the internet in any case.

I intend on building it offline and then rent some server space for me to upload to.

So in short i have not got it up and running.

Ok. Trying to pull the package down from the ubuntu repos isn't going to work with no network connectivity. You can download the package using any OS:

[http://packages.ubuntu.com/natty/mediawiki]("http://packages.ubuntu.com/natty/mediawiki")

Copy it onto the server via USB flash. To install it:

```
cd /<whereever you put the deb file or path to the usb flash>
sudo dpkg -i mediawiki_1.15.5-3_all.deb
```

If there are dependencies then dpkg will ask for them. You will have to manually download those packages too. You can install multiple packages in one go via:

```
sudo dpkg -i *.deb 
```

Even if you get this working you are likely to get quite a lot of grief if you are planning to just copy the final OS image to a machine with completely different hardware. Also you will have to learn to sort out the networking. Personally I would get that sorted first as you will need to be able to do that on the real server and it will make your life a lot easier in the mean time.

---

