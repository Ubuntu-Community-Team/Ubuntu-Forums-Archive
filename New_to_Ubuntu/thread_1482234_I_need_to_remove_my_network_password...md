---
title: "I need to remove my network password.."
date: 2010-05-13
forum: New to Ubuntu
---

### Post by request_another on 2010-05-13
Ok let me explain my predicament. I have a ubuntu machine running on my local network and another windows 7 machine on the network. The windows pc is sort of the HUB, because that's where i keep a lot of files to share between my pc and the windows pc. 

Now the thing is, when i go into network on ubuntu, and i see the windows pc there, it asks for a password to connect to the share folders. I asked my sister to write her password from her account because i didnt have my account any more on windows, but now i can see her personal files which she doesnt like. The thing is when i inserted the password, i set the option to remember forever. I want ubuntu to forget it so that i can create my own account on windows 7 and have ubuntu sync with my account and not my sisters.

is this possible? sorry for the wall of text :P If something's not understood i can rephrase it.

---

### Post by spiky001 on 2010-05-13
Itake it you are using samba? Have a look at this

[http://www.randyjensenonline.com/blog/quick-samba-tip-locations-samba-shares-ubuntu](http://www.randyjensenonline.com/blog/quick-samba-tip-locations-samba-shares-ubuntu)

---

### Post by request_another on 2010-05-13
i typed in those commands but i didnt find what i need. Could u please guide me here, im rather new to this. In the smb.conf file i didnt find the section for the password. And for the usershares i dont think that file location exists.

---

### Post by Morbius1 on 2010-05-13
Applications > Accessories > Passwords and Encryption Keys > Passwords Tab

Expand the "Passwords: login" entry and you should see the the entry for the remote share

---

### Post by request_another on 2010-05-13
thank you so much, that did the trick

---

