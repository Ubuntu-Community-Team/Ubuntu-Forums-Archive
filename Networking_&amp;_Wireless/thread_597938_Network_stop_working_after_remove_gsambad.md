---
title: "Network stop working after remove gsambad"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by pemimpin on 2007-10-30
Sorry if my english are not very good....

I got some problem here :

1 - When I use Windows to access my shared folder in Ubuntu. It keep asking for username and password? so I put my username and password (same I put in login screen) but i not working.

2 - I thought maybe i need use some GUI for setting networking on Ubuntu. Then I installed gsambad. Later, I found the GUI are so advanced that I not too 'genius' to use. Then, I remove it. Suddenly, when I click Places > Networking nothing of Windows Network has found.

I click refresh button over and over again. Restart my computer. But it still same. I think maybe gsambad over-written for Networking config file.

3 - I put my printer on Ubuntu. I cannot find way how to share with windows networking. When i put my printer on windows. Ubuntu can use it nicely. So, how can i share printer on Ubuntu to Windows ?

Hope anyone can help me...:popcorn:

---

### Post by daengbo on 2007-10-31
Answering #3. Go to System -> Administration -> Printing and click to share your printer.

---

### Post by pemimpin on 2007-10-31
i try that before. but the printer can not be access because it always ask username and password tu enter my Ubuntu share folder.

before this, it never happen (in ubuntu 7.04). maybe there is something to do with implementing AppAmor . Some sort of firewall. Maybe.

---

### Post by StefanPieter on 2007-11-04
I have the same problem. i can see any network users now. This GSAMBAD is far to advanced for me. How do i get it so that i can see the networks again and that they can see me?

---

### Post by chris2028 on 2008-02-23
me here, same problems...
i m trying to use it..... GSAMBAD 0.1.6

basically i m reading the .conf now...........

and I think the GSAMBAD is more likely for advance person ~~! (server base)
for the mean time, if you can't / not willing to use it...
you can sudo cp the old samba.conf  to /etc/samba/smb.conf to replace it....

somthing like the following
sudo cp      /etc/samba/smb.conf.gsambad.old     /etc/samba/smb.conf

and it should use the old samba.conf ......................... now you need to restart your Ubuntu... 
and remove the GSAMBAD if you need to.

---

