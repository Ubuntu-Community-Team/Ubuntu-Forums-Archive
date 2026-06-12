---
title: "Samba problems with encrypted password requirement"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by booberandpuzz on 2008-05-02
I'm completely new to Linux and have built a simple box based on Ubuntu 8.04 to serve as SOHO fileserver.  I installed Webmin in an attempt to easily, quickly get samba shares available for workstation backups.

I have opened the **System/Users and Groups** module and there see a long list of users, including the three I've created. When I open either root or one of my users, the default password requirement is pre-encrypted password and the field is populated with cryptic-looking 13 characters. I've tried several times to change this option to Normal password, tried it populating the password, leaving it blank, but whichever I try, the change doesn't 'stick.' It comes up every time I reopen it set back to pre-ecrypted. I've changed it as root, as my own admin-level user, same result.

Furthermore, if I try mapping or logging into a share from a Windows machine using either this encrypted password or the normal one, it doesn't work either. I also tried logging in from Windows Map Drive dialog as a "different user" and specified my Linux uid/pwd, to no avail.

Where I'm failing here is not comprehending the basic framework and interrelation between a multitude of Samba configuration options. When I'm studying the books' sections on configuring Samba, I don't know for example, what would make me decide this machine is a Primary Domain Controller or not, but for a SOHO, with as many as six users, my gut says no. Two of the so-called "server" books don't even have an index listing for PDC. If that has little to do with my issue, good clue as to how much of a n00b I am ... and how lost.

I've searched through the several recent titles I bought, **Using Samba, Linux Quick Fix Notebook, Beginning Ubuntu Server Administration** and I'm coming up even more confused. I want to learn this, but I'm a bit overwhelmed by the sheer volume of configurable options, probably only a few of which pertain to my situation. Don't get me wrong. It's ENCOURAGING to me that there are so many user-manageable aspects of this O/S.  However, I'm admittedly at the very base of the learning curve and just need a clue as to where to start on this one. Even though I'm trying to use GUI tools like webmin and SWAT, I believe this is basically a Samba configuration issue, and with some guidance, I see that it could be more illuminating for me to approach the solution from the command line.

I do want to ultimately run this headless and also support remote secure access for file transfer.

Also, I posted this a few days ago on LinxQuestions.org but have received no replies.

---

