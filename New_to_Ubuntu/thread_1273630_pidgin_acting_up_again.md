---
title: "pidgin acting up again"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by misswham on 2009-09-23
I have been noticing for the past week when I send someone a message, they sometimes see it and sometimes dont.  It appears that they were online and then it says they are off and the person i am chatting with never logged off.  Today it happened and the person contacted me 5 mins later saying "r u here r u here" and i said why did u log off and he said he didnt.  I have also sent messages to people offline that they never got.  i doubt all of the people are lying.  Also someone asked me a question and I answered it and they said "r u gonna answer my question"  and i said i did cant u see it.  I told them to scroll up and they did and the answer wasnt there but it was on my end.  What does anyone think could be happening?

by the way i was using yahoo

---

### Post by misswham on 2009-09-23
does anyone have the same problem

---

### Post by earthpigg on 2009-09-23
pidgin was having exactly this problem with yahoo several months ago. it has since been fixed.

1 - update your system, ***restart pidgin*** (restart whole computer if it tells you to), and then test it.

2 - if the most up-to-date official pidgin from ubuntu does not work, try downloading/installing pidgin from getdeb.net. make sure you get the ubuntu version and architecture correct. download the .deb files to your desktop and double click on them. [http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by misswham on 2009-09-23
I have accessed the link above and i see that i have 2.6.1 and this is 2.6.2.  it is asking me to remove the current version.  do i go to add and remove to remove it or synaptic?  also i dont see a version on the link that says hardy specifically and i dont understand what is architecture.

this is what i see to download

 Download:   pidgin  (560.8 kB)  ,  libpurple0  (1.7 MB)  ,  libpurple-bin  (105.2 kB)  ,  pidgin-data  (7.3 MB)  

which one am i supposed to click?

---

### Post by misswham on 2009-09-23
i just removed pidgin all of it that says 2.6.1 and now when i double clicked the deb file it says 

Error:  Dependency is not satisfiable: pidgin data

what do i do now?

---

### Post by zeroseven0183 on 2009-09-23
I would suggest downloading the whole thing in [http://www.pidgin.im](http://www.pidgin.im)

---

### Post by mathay on 2009-09-23
You need to install the additional dependencies in order for Pidgin to run properly. Did you install the pidigin-data and pidgin-dev files?

---

### Post by earthpigg on 2009-09-24
> Download: pidgin (560.8 kB) , libpurple0 (1.7 MB) , libpurple-bin (105.2 kB) , pidgin-data (7.3 MB) 
> Error: Dependency is not satisfiable: pidgin data

the install pidgin-data first :D

---

### Post by misswham on 2009-09-27
I removed pidgin from synaptic again and when i click the data file to install first i get this message

An older version is available in a software channel

Generally you are recommended to install the version from the software channel, since it is usually better supported.

what is the software channel and should i do it or just go ahead with the download of the data and do i download all packages in a certain order?

---

### Post by misswham on 2009-09-27
ok now i have gone ahead and installed pidgin data successfully and now when i try to download the other packages i am still getting 

Error: Dependency is not satisfiable: libdbus-glib-1-2

cant download the last 3 packages.

has anyone else upgraded to 2.6.2?  from 2.6.1?  if so did your problems persists?  

in 2.6.1 people are saying it shows that i have logged off when i havent and i am sending messages and 20% arent shown to the recipient and people are being shown that they are typing and sometimes it doesnt come through and from time to time it will just log off without my logging off.

---

### Post by misswham on 2009-09-27
pleeze can someone help?

---

### Post by earthpigg on 2009-09-27
> **misswham said:**
> ok now i have gone ahead and installed pidgin data successfully and now when i try to download the other packages i am still getting 

Error: Dependency is not satisfiable: libdbus-glib-1-2

cant download the last 3 packages.

then open synaptic, and install libdbus-glib-1-2 :D

using apt-get does what is called 'resolving dependencies' automatically. that is one of the great things about linux package management, when it works for you.

in this case, since ubuntu's repos don't have the most up-to-date stuff, you need to resolve dependencies on your own.

basically: if it tells you it is missing something it depends on, go ahead and install it.

download all the .debs there:>  pidgin (560.8 kB) , libpurple0 (1.7 MB) , libpurple-bin (105.2 kB) , pidgin-data (7.3 MB) 

and trial-and-error which order they need to be installed in. if it tells you to install a package that isn't one of those, go ahead and find it in synaptic.

background for why this is different than Windows:

one of the parts of the "Unix Way" is to make ***one small program that does one task very well and make it work well with other programs.*** like 'libdbus-glib-1-2'. we aren't programmers so we don't need to know what it does, but clearly it does ***something***, right? hence, the other package is 'dependent' on it being installed to work.

then, a dozen or a hundred other programs can rely on libdbus-glib-1-2.... instead of re-inventing the wheel, anyone writing a program that needs the functionality of whatever-the-heck libdbus-glib-1-2 does does can use the existing libdbus-glib-1-2 instead of starting over.

that also means that if you have 30 programs installed that rely on libdbus-glib-1-2, you dont need libdbus-glib-1-2 installed 30 times. just once, and the other programs can all use it.



now, when you use apt-get install, it automatically figures this stuff out for you and you don't need to worry about it. 'figuring this stuff out' is called '**resolving**' the dependencies. 

all you are working through right now is doing this yourself, since we aren't using apt-get install.

you will need to install those 4 .debs from getdeb.net in a certain order. before you start, you may need to install another package or two from synaptic. all you need to do is read what it is telling you you need to install :D


does all that make sense?

---

