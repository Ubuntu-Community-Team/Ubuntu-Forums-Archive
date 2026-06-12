---
title: "ubunto 9.10 network configuration problem"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by Maria_1980 on 2010-05-31
[COLOR=black][FONT=Verdana][SIZE=2][FONT=Arial]Hello Everyone,[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2][FONT=Arial] [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2][FONT=Arial]I am newbie in linux, can anyone please help me through the following problem. I was asked to config couple of computers and add them to the network. I installed linux 9.10 on two clients and went through the following steps as I was told to do. [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2][FONT=Arial][FONT=Symbol]·[FONT=Times New Roman] [/FONT][/FONT]Set up NIS and NFS on the client system. The instructions I used are here:  the following bits on the client PCs: [/FONT][/SIZE]
[SIZE=2][FONT=Arial]1.    Install the appropriate packages:[/FONT][/SIZE]
[FONT=Courier New][FONT=Arial][SIZE=2]sudo aptitude install portmap nis nfs-client ssh[/SIZE][/FONT][/FONT]
[FONT=Arial][SIZE=2]Enter [COLOR=darkred]CompanyNISdomainName[/COLOR] as the NIS domain. [/SIZE][/FONT]
[SIZE=2][FONT=Arial]2.    Edit /etc/hosts.allow to add a line like:[/FONT][/SIZE][FONT=Courier New]
[FONT=Arial][SIZE=2]portmap : [COLOR=darkred]ServerIP Address[/COLOR][/SIZE][/FONT][/FONT][FONT=Arial][SIZE=2] [/SIZE][/FONT]
[SIZE=2][FONT=Arial]3.    Edit /etc/passwd to add a line at the end saying:[/FONT][/SIZE][FONT=Courier New]
[FONT=Arial][SIZE=2]+::::::[/SIZE][/FONT][/FONT][FONT=Arial][SIZE=2] [/SIZE][/FONT]
[SIZE=2][FONT=Arial]4.    Edit /etc/group to add a line at the end saying:[/FONT][/SIZE][FONT=Courier New]
[FONT=Arial][SIZE=2]+:::[/SIZE][/FONT][/FONT][FONT=Arial][SIZE=2] [/SIZE][/FONT]
[SIZE=2][FONT=Arial]5.    Edit /etc/shadow to add a line at the end saying:[/FONT][/SIZE][FONT=Courier New]
[FONT=Arial][SIZE=2]+::::::::[/SIZE][/FONT][/FONT][FONT=Arial][SIZE=2] [/SIZE][/FONT]
[SIZE=2][FONT=Arial]6.    Edit /etc/yp.conf and add the line:[/FONT][/SIZE][FONT=Courier New]
[FONT=Arial][SIZE=2]ypserver [COLOR=darkred]ServerIP Address[/COLOR][/SIZE][/FONT][/FONT][FONT=Arial][SIZE=2] [/SIZE][/FONT]
[SIZE=2][FONT=Arial]7.    Edit  /etc/fstab and add these two lines:[/FONT][/SIZE][FONT=Courier New]
[FONT=Arial][SIZE=2]thunderpants:/home      /home   nfs     rw      0       0
thunderpants:/srv/shares/admin /shares/admin    nfs     rw      0       0[/SIZE][/FONT][/FONT][FONT=Arial][SIZE=2] [/SIZE][/FONT]
[SIZE=2][FONT=Arial]8.    Restart NIS:[/FONT][/SIZE][FONT= ]
[FONT=Arial][SIZE=2]sudo /etc/init.d/nis restart[/SIZE][/FONT][/FONT][FONT=Arial][SIZE=2] [/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[/FONT][/COLOR][COLOR=black][FONT=Verdana][SIZE=2][FONT=Arial] I have done all the steps, at the end I tried to look at share folder. [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2][FONT=Arial] [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2][FONT=Arial]1. one of the computers hanged, I restart it. But then system is not boot completely. the screen shows that there are some problems with the server configuration and ICEauthority, and also shows following message:[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2][FONT=Arial]/usr/lib/libgconf2-4/gconf- sanity- check one or more of the mounts listed in ect/fstab cannt yet be mounted: 
/home: waiting for [COLOR=darkred]ServerIP Address[/COLOR]:/home
/shares/admin: waiting for thunderpants: /srv/share:/admin[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2][FONT=Arial] [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2][FONT=Arial]2. Second computer said does not recognise the client password to let it connect to the share folders. !!??? I can see the server on the network place area but ...!!!!??? [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2][FONT=Arial] [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2][FONT=Arial]Do I need to made a change on the server? or what? help pls (I already asked this question from the server administrator But didnt get clear answer just was told that there should not be any need to change the setting on the server)!!!![/FONT][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2][FONT=Arial] [/FONT][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2][FONT=Arial]I would appreciated if anyone can give me an idea pleaseee. [/FONT][/SIZE][/FONT][/COLOR]
[FONT=Arial][SIZE=2] [/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT]

---

### Post by Marky- on 2010-06-02
I'm having the same problem setting up NIS on 10.04.  Can anyone help?

---

