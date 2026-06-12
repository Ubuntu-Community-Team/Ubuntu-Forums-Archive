---
title: "Help with Sadms and PAM"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by gali98 on 2008-02-25
Hi. I work for a school and am using sadms (Samba as Active Directory Member Server/Station [http://sadms.sourceforge.net/](http://sadms.sourceforge.net/))
I have got everything to work and I recommend this to anyone trying to get ubuntu to authenticate on an AD Domain. However I am having a problem automatically mount home drives. You have an option to mount with PAM which works great, however here is the problem.

We have a server with home directories on it: Bisdnas
On this server we have the staffhome folder with all the staff and the stuhome folder with subfolders with each grade (Class09 class10 class11 and  so on)
so basically we have these folders that need to be included in a search of home directories:
//bisdnas/staffhome
//bisdnas/stuhome/                              (there are some homes in the root)
//bisdnas/stuhome/classxx                  (where xx equals class number 09, 10, 11, or whatever)

but the PAM options (when you click "install PAM modules" in the menu) are only "server" and "home share."
So you can only enter the server (bisdnas) and one of the needed folders (/bisdnas/staffhome but you actually just type "staffhome/*"
And that works fine if you are staff, however these are going to mostly be for students, and another problem arises that I cannot figure out: it won't work with sub-sub directories. (Don't know if that's right grammer) i.e /bisdnas/stuhome/classxx. 
That may be a requirement in PAM.
So I'm not one to post without trying out other stuff. I tried creating shortcuts to the directories:
I made a shortcut to //bisdnas/stuhome/class10/kp4707 (my student account) and placed it in both  //bisdnas/stuhome and //bisdnas/staffhome however neither worked and I didn't figure they would because I know Windows shortcuts work differently than linux ones do. (I guess they're not really shortcuts but more of links.) 
So I figured I would just go in with nautilus and use the link there in the context menu, but I get a error message to the tune of "cannot create a link because the path is smb://bisdnas/blahblah"
which I guess means that linux can't create a link on a windows server. (or with the smb protocol)
So I finally came here to find some help. I know this is a lot of information I put here, but I wanted to cover everything, and I know the whole authentication scene is kind of guess and check work, but I figured someone out there will have an answer for me. Thanks in advance,
Kory

Note: I also know that there might be better forums to post this kind of stuff so any referrals would be appreciated.

---

### Post by gixxer.rob on 2008-02-26
Hello Gali98,

i too work at a school and am trying to get Sadms working the way i want it with some windows servers. Can i ask, if there was anything special that you did to get the AD user home directory to mount ? 

When i do a authentication test from the diags menu, the auth section works fine but it returns an "mount error 113 no route to host " error. The end result of this is when the AD user logs in no AD home is mounted for them. I don't seem to be able to mount it manually..

Any help would be great.

---

### Post by gali98 on 2008-02-26
I don't really know... It just kind of worked. On the info page I just used the autofind (or whatever it calls it) to find most of the stuff and entered the rest myself. Were you able to join? I know it is PAM that mounts the directories so under the PAM menu make sure to uncheck "test only" and then do "install Pam modules".
in the dialog that comes up you have to enter your information. I'll use mine above as an example.
my staff home is //bisdnas/staffhome/whatever user logged in.
So I would put "bisdnas" in the server box
and "staffhome/*" in the other box.
Notice the placement of the "/"s. the two before bisdnas and the one after it are implied by the program.
Hope this helps... If not post again and maybe I can.
Kory

---

### Post by bolivartech on 2008-04-29
This may be a alot of work, but we have the same setup and I was forntunate that the man in charge of creating the users home directories on the windows server was able to forsee an issue with embedded home directories. What he did was create the users with in both \\servername\users\staff\username and \\servername\users\students\username then went to the server and created a share \\servername\username$ and then changed then changed the users home in AD to \\servername\username$ . This gives the user access rights to the original folder and if you set the rights for the share correctly by removing Everyone and adding username and administrator, then you have a root level share that can be accessed by PAM. Yikes that's a lot of work. I don't know if there is a way to script that but I don't know anyway to get PAM to read into those folders otherwise. I'm getting ready to try SADMS out myself because my new install of ubuntu 8.04 using Likewise-Open is causing me too much grief with pam_mount. If SADMS works then I'm sold and in business. I could almost introduce Linux on Desktop, not just thin clients then! Here's hoping. Let me know if that works for you, if you can try it on just one user.

---

