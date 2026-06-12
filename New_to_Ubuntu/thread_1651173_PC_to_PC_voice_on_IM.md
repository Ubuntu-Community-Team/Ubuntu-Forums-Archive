---
title: "PC to PC voice on IM"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by jackwilson on 2010-12-22
When I used to have Windows XP.  I had yahoo messenger 10 and was able to talk to my contacts with PC to PC voice chat.
I downloaded yahoo messenger 10 and installed it with wine program loader. When I sign in it says there is something wrong with my Internet connection. There is a troubleshoot button, but it does not do anything. My Internet connection works for everything else.
The empathy IM says I can make voice calls, but my contacts that I was able to voice chat with on yahoo IM do not have a microphone by them to do voice chats. The right click menu on my contacts will only let me chat or edit the rest of the items are not highlighted. The empathy FAQ says the voice is not available for yahoo contacts.
Anyone tell me why not?
Google talk is supposed to be compatible with empathy but, I do not know how to set that up either.
Thanks in advance,
jackwilson

---

### Post by amjjawad on 2010-12-23
Not sure if that will be so much help but try "[Pidgin]("http://www.pidgin.im/")".

---

### Post by mastablasta on 2010-12-23
Try Pidgin messanger for better connectivity with yahoo. It is also availabekl for windows i believe.
 
Another thing you can try is Gyache improved: [http://sourceforge.net/projects/gyachi/](http://sourceforge.net/projects/gyachi/)
 
which is an attemt to have a compatible yahoo client for linux. cause yahoo dumped their linux version some time ago.
 
then there is always Skype for linux (i suggest you donwload a .deb file form their site and install it like that). works well video&voice.

---

### Post by jackwilson on 2010-12-23
I downloaded  gyachi-1.2.7. tar.gz  from [http://sourceforge.net/projects/gyachi/](http://sourceforge.net/projects/gyachi/)
How do I install? 
when I type 
tar xfvz *tarball_gyachi-1.2.7.tar.gz* terminal says:  No such file or directory.

---

### Post by mastablasta on 2010-12-23
you can extract it and then read the install.txt file:

> 	Steps for building a gyachi executable

1) use the autogen script to generate a configure script:

	./autogen.sh

2) run configure, with any options that you might prefer:

	./configure --disable-rpath --enable-maintainer-mode --prefix /usr

3) To generate a Fedora/RedHat spec file

	make gyachi.spec

   To build an image that will be installed over existing executables
   (not recommended):

	make
	make install

or maybe just run instal.sh :-O

---

### Post by jackwilson on 2010-12-23
I downloaded gyachi-1.2.7.tar.gz from[ http://sourceforge.net/projects/gyachi/]("http://sourceforge.net/projects/gyachi/")
How do I install the program file?
I opened terminal and typed:   tar xfvz tarball_gyachi-1.2.7.tar.gz  and terminal told me No such file or directory.
jackwilson

---

