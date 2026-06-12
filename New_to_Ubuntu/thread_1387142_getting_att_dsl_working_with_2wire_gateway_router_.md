---
title: "getting att dsl working with 2wire gateway router and ubuntu"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by Lucas156 on 2010-01-21
Hey there I just had problems getting my dsl working through a self install through att but I figured it out plus with a little help from technical support so I wanted to help someone out if they have this problem in the future.  I referred to this guide at web address and it did help a lot to get me started [http://www.obviously.com/tech_tips/Yahoo_DSL_setup_no_CD.html](http://www.obviously.com/tech_tips/Yahoo_DSL_setup_no_CD.html) 

The issue that I had to call technical support for is I did all this but still had no internet.  The step they left out is this-after you register your username and password and everything it told me that my system requirements did not meet the criteria for wireless installation.  I don't need to install anything Im just getting a feed to my computer is what Im thinking.  Well, you have to go back to the page where you input the temporary login information [email]sbcyahooreg@sbcglobal.net[/email] and password sbcyahooreg.  Erase that and put your new username and password you just registered with att and hit next.  Internet should suddenly work.  no cd or anything required.  :)  I have Ubuntu and again a 2wire gateway so this may not work for other setups but I hope this can help someone.  Thanks

Lucas

---

### Post by alphasoup on 2010-04-22
I found the following message useful:
[http://www.att.com/t5/Account-Registration/DSL-setup-on-unsupported-Operating-Systems-such-as-Linux/m-p/3574](http://www.att.com/t5/Account-Registration/DSL-setup-on-unsupported-Operating-Systems-such-as-Linux/m-p/3574)
While using a Proline modem the setup from Ubuntu worked a bit differently than on this post for me. This is what worked:
1) Plug Ubuntu into the modem without rebooting via eth2
2) (Refresh your network DHCP) ifconfig eth2 down; ifconfig eth2 up
3) eth2 was given and address on private subnet of the modem with gateway as 192.168.1.254 -- to check your IP and gateway address: ifconfig eth2; netstat -rn;
4) open Firefox and if you do not get automatically redirected to an AT&T setup page, then use one of [https://sbcreg.sbcglobal.net]("https://sbcreg.sbcglobal.net/"), or [www.att.com/internetaccount]("http://ubuntuforums.org/www.att.com/internetaccount"), or [https://attreg.att.net/dsltech](https://attreg.att.net/dsltech) -- tried all of them with various results at times... This redirects the first time to a page where you can enter phone (or alternate as directed) number and create personal account login / password.
5) Then manually point Firefox to your modem address, e.g. [http://192.168.1.254]("http://192.168.2.254/"). The modem was pre-setup with usename/password = [EMAIL="attreg@att.net"]attreg@att.net[/EMAIL]/attreg account. The problem with this account is that it will turn every pages you access to a redirect that asks you to login and then checks your computer to see if it is M$ or Apple... Each time you will find that your computer is not supported and you are stuck.
6) You need to replace the (e.g. Proline) modem login and password by your own personal account created the first time above in 4. To change this I had to disconnect the modem using the "disconnect" button on a page from the modem at [http://192.168.1.254]("http://192.168.2.254/"). Then eventually it came up with a prompt to enter login and password (the personal account). 
7) The modem was then still stuck with a non networking configuration. Restarted the modem from Firefox menu, then had to manually power off/on modem before a new network connection was created (there are advanced options you can use with care to select the type of network connection you want). After this the modem correctly logged-in using the newly stored personal account/password. Then the annoying page redirect to check for exclusive M$ or Apple system** stopped**.
8. Still had to reset my network connection (no need to reboot): ifconfig eth2 down; ifconfig eth2 up; for Ubuntu to sync with new network setting. Then immediately Firefox had access to the Web then setup a firewall just in case (have external IP access): sudo ufw enable.
9) Internet was connected and Ubuntu working again...
10) The Proline modem has not routing rules and no local LAN or WLAN, so inserted another router behind the Proline DSL modem.

There is no need to add software (to Ubuntu?) to get connected. The procedure is confusing due to obnoxious redirects to some software download page, the key is to realize that a valid personal account must be stored in the modem. If that does not work you can revert  your modem to original login/password [EMAIL="attreg@att.net"]attreg@att.net[/EMAIL]/attreg.

---

### Post by fatpat812 on 2010-08-05
easiest way to get att dsl to work is download wine if you dont already have it. sudo apt-get wine. the go to firefox.com and download the latest windows version. go to your downloads folder and right click the firefox installer, open with wine program loader, install windows firefox via wine. click applications, wine, programs, firefox. when the browser comes up follow att's steps windows version browser fools att, gets internet all set up and saves your username and password in the modem for you. then you can delete windows firefox if you wish and use any browser of your choice. that is all. worked great for me and skipped all the confusing steps. i use google chrome and firefox both linux native and no problems.

---

### Post by cjack007 on 2010-08-06
there is a issue with dsl connections.
you can either follow fatpat's method or boot into windows if you have and set it up from there.

---

