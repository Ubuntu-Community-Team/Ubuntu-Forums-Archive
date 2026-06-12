---
title: "AutoApt question thousands of windows normal?"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by gognos on 2009-09-12
Hi guys just had a quick question about AutoApt

I wanted to compile the newest vlc 1.0.1 ubuntu repository is 0.9

I did the following 

>  sudo apt-get install build-essential checkinstall >  sudo chown yourusername /usr/local/src Of course Changed your user name to my user name 

>  sudo chmod u+rwx /usr/local/src This information followed from here

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Next i did what was needed for auto-apt

>  sudo apt-get install auto-apt
sudo auto-apt update
sudo auto-apt updatedb && sudo auto-apt update-local As per instructions here [https://help.ubuntu.com/community/AutoApt](https://help.ubuntu.com/community/AutoApt) 



I downloaded the vlc 1.0.1 tar.gz file moved and extracted it in the /usr/local/src folder 


next 

cd /usr/local/src/vlc-1.0.1
auto-apt run ./configure
make
sudo checkinstall 

following instructions here [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)


now for my problem auto-apt ran first opened a secondary terminal window in which it started checking everything. however every time it checked an item it opened another terminal window basically asking for password it ended up opening hundreds if not thousands of these windows.It appears to find if either this or that is installed without me actually needing to enter my password but as its auto checking for eveything all windows stay open.finally when everything was checked i was able to type my password into the final window opened.It started downloading packages needed and such and basically failed because it couldn't find 2 packages. i was given the 2 missing packages names and was able to get them with apt-get install whatever-whatever-was-missing copiled without auto-apt run   just  normal ./configure
make  sudo checkinstall and all worked

Is what i did right ? i mean all those windows basically crashed ubuntu 9.04 2gig ram. Is it normal for all those windows just to keep opening when using auto-apt ??

---

### Post by yeats on 2009-09-12
I've never used auto-apt, so I don't have advice about the multiple windows problem (except that NO, that does not sound like normal program behavior).

What is your end goal here?  Are you just trying to install the newest version of vlc?

---

