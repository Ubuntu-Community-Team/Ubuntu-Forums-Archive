---
title: "making update dvd for pc that don't have internet connection"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by chinmay3 on 2010-11-09
[COLOR=Magenta]hello friends.[/COLOR]
[COLOR=Black]Recently I have made fresh installation of ubuntu 10.04 on my computer. Then I have downloaded updates whose size is about 300 MB. But while installing updates power gone and thereafter I can't login into as both mouse & keyboard  [/COLOR]are inactive. I can use both these with live cd but not with my installed ubuntu. 
[COLOR=Red]So I have decided to reinstall ubuntu erasing previous. But I don't want do delet updates that I have [COLOR=Purple]downloaded spending about 6 hr. on 15 KBpS connection. [/COLOR]
[COLOR=Black]so anyone can tell me location of directory where downloaded updates are stored. Is it possible to burn these updates on dvd or cd & then use it for updating my reinstalled os. [/COLOR]
please be quick to reply me . I can't live without UBUNTU.:confused:
[/COLOR]

---

### Post by theozzlives on 2010-11-09
The updates are fixes and such to software and libraries. To the best of my knowledge, you'll have to download them in some form or another. It's feasible that you can download them from a reasonable connection and burn to CD/DVD. If it's a laptop, you can connect at the library or a cafe and update it.

---

### Post by plucky on 2010-11-09
> so anyone can tell me location of directory where downloaded updates are stored.

**/var/cache/apt/archives**


Good Luck

---

### Post by prshah on 2010-11-09
> **chinmay3 said:**
>  
[COLOR=Red]So I have decided to reinstall ubuntu erasing previous. But I don't want do delete updates <..> so anyone can tell me location of directory where downloaded updates are stored. Is it possible to burn these updates on dvd or cd & then use it for updating my reinstalled os. [/COLOR]

As already stated, the downloaded updates are in the /var/apt/cache/archives directory. You can save the entire directory to either a pen drive or a CD/DVD-R/RW.

Post back if you want to know the command-line-fu required to write CDs/DVDs.

Alternately, I would suggest that you can try to recover the system: it's pretty easy to recover from an interrupted upgrade.. please see: [Hardy is wonderful...]("http://ubuntuforums.org/showthread.php?t=780531") for tips on how to recover from a failed/interrupted upgrade. I would suggest you try this first.

---

### Post by chinmay3 on 2010-11-09
[COLOR=DarkOrchid]Thanks everybody!!
I got all those packages I have downloaded. 
[COLOR=Black]They are all in  " .deb" format. do I use gdebi package installer & installl them one by one or there is any other good method to do that ?[/COLOR]
:KS
I would like to recover system but to enter command you require an active keyboard. as my keyboard & mouse are non-functional with that installed os I can't use command line interface.  Is there any method to repaire it using live cd ? with live cd  both keyboard & mouse functions well.
[/COLOR]

---

### Post by chinmay3 on 2010-11-09
> **chinmay3 said:**
> [color=darkorchid]thanks everybody!!
I got all those packages i have downloaded. 
[color=black]they are all in  " .deb" format. Do i use gdebi package installer & installl them one by one or there is any other good method to do that ?[/color]
:ks
i would like to recover system but to enter command you require an active keyboard. As my keyboard & mouse are non-functional with that installed os i can't use command line interface.  Is there any method to repaire it using live cd ? With live cd  both keyboard & mouse functions well.
[/color]
[color=navy]just because something is difficult, doesn't mean you shouldn't try[/color]....
It means you should just try harder.

---

### Post by PFN on 2010-11-09
just copy the .deb files to /var/cache/apt/archives/ in your new installation and when you run update you dont need to do re-download them unless new upddates available

---

### Post by Nightstrike2009 on 2010-11-09
Have you tried apt-on-cd?

Its in the repo's and provides a GUI for apt-cache back ups (Installed programs) so you dont have to redownload them, I use it its easy to use and works fine for me, It's doesn't install all programs back as standard but when you reinstall via either terminal or software manager you shouldn't need to download again from net (I use terminal for install/uninstall), Hope that helps you.

---

### Post by chinmay3 on 2010-11-10
since i am booting from live cd . I am unable to copy updates on my pen drive. Is there any command to do that?  I have tried login in as "chinmay " which is root user for my system but it results in authentication failed. I am sure about about my login name & password but yet I am unable to login as root user.

---

### Post by PFN on 2010-11-10
After you boot with live cd insert your pen drive and it will automatically mount and show you a icon on desktop.
Then mount your ubuntu instaleld partition from Places--> Removable media
It will open your ubuntu partition in file browser.
Go to /var/cache/apt/archives/ and copy all .deb files then paste into your pendrive .
If there will be any permission problem, then open a terminal and type "sudo nautilus" without quotes and press enter.
This will open the file browser with root access.
Then you can copy the files.
Post with more details if problem not solved

---

### Post by chinmay3 on 2010-11-10
Thanks all. 
finally i succeed to copy updates on pen drive. 
Also I solved my log in problem without reinstalling ubuntu. I just removed keyboard & mouse before starting pc. & when I come to login screen I plugged both. surprisingly both start functioning. Then i logged in & followed command as told by " prshah" . & now everything working fine. 
Once again thanks everybody for such a nice support.:guitar:

---

### Post by prshah on 2010-11-11
> **chinmay3 said:**
> just removed keyboard & mouse before starting pc. & when I come to login screen I plugged both. surprisingly both start functioning. 

Good to know that things worked out fine. However, here is an important tip: do NOT plug/unplug PS/2 devices into a running (turned on) system; there is a VERY REAL chance that you can damage your motherboard.

USB devices are OK. Just a tip for the future, and for others stumbling across this post.

---

### Post by chinmay3 on 2010-11-11
Thanks for advice:popcorn:.

---

