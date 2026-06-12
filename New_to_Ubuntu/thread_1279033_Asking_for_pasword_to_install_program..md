---
title: "Asking for pasword to install program."
date: 2009-09-30
forum: New to Ubuntu
---

### Post by Zundap on 2009-09-30
Can anyone please help, i have installed UBUNTU, but i am unable to view youtube, i get an error message saying that i require flashplayer, that downloads no problem, but when i try to install it, i get asked for a password.

I have tried the password that i used to install UBUNTU, and not is not the correct password, could anyone tell me how i find what the password is?

Thanks

---

### Post by halitech on 2009-09-30
it should be the same password you used to log into the system with as long as you are the first created user on the system.

---

### Post by Mark Phelps on 2009-10-01
Did you download an .exe file and are you double-clicking it as an attempt to install it? If so, that will not work because that's an MS Windows executable file -- and that will not run in Ubuntu.

---

### Post by nhasian on 2009-10-01
Zundap, open a terminal by going to Applications->Accessories->Terminal.

in the terminal copy and paste:

```
sudo apt-get install ubuntu-restricted-extras
```

also if you need dvd playback, copy and paste this line as well:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

for more info see:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Zundap on 2009-10-15
Sorry for being late to reply but i have had quite a few problems latelyThanks for the advise nhasian, but ended up having to reinstall, i ugraded to 9.04 and it screwed things up big style, so i reinstalled, strangely this time it accepts the password ok.


I have managed to download the youtube recomanded flash player, but i still can not play youtube video's, the page loads but the actual video part of the page is not there.

Would anyone have any idea's on this problem, Thanks.

---

### Post by kayvortex on 2009-10-15
> **Zundap said:**
> Sorry for being late to reply but i have had quite a few problems latelyThanks for the advise nhasian, but ended up having to reinstall, i ugraded to 9.04 and it screwed things up big style, so i reinstalled, strangely this time it accepts the password ok.


I have managed to download the youtube recomanded flash player, but i still can not play youtube video's, the page loads but the actual video part of the page is not there.

Would anyone have any idea's on this problem, Thanks.

Did it install OK? I seem to remember flashplugin not installing when clicking on the install missing plugin message. I'd recommend following *nhasian*'s suggested commands to make sure the flash player installs. Enable the multiverse repo, enter the command and post what appears.

---

### Post by sloggerkhan on 2009-10-15
Just install the flash deb from adobe's website. I've yet to have any problems with it.

---

### Post by Tclarkie on 2009-10-15
use adobe flash, linux's (GNU's) version isn't good, thats coming from a Stallman Clone

---

### Post by Tclarkie on 2009-10-15
[http://ubuntuforums.org/showthread.php?t=1230177](http://ubuntuforums.org/showthread.php?t=1230177)

---

### Post by sandyd on 2009-10-15
are you using x64 bit?
post output of
```

uname -r

```if its 64 bit, then.
```
wget -c http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar xvfz libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
mv libflashplayer.so /usr/lib/firefox/plugins/libflashplayer.so
rm flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```

---

### Post by Zundap on 2009-10-16
I am sorry t o say that i have thrown the towel in with ubuntu 8.04, i was getting all sorts of problems, so i decided to install 9.04 instead, i just hope that i dont get the same problens again or i might end up going back to windows.

on the last re install of8.04, Everything worked ok to start after about 1/2 hour or so, the word processor would not work properly. It worked ok three or 4 times, then i could open a new page ok, but when i went to open an old file that i had imported from my other windows hardrive, it woukld crash, so i could not open my old documents.

Once again firefox worked ok to start with, but then Round about  the same time, as the word processor started playing up, i could open a web page ok, but when tried to scroll down a page, only about a tenth of the page scroled, and when i tried to scroll back up the page only the about the top tenth of the page scrolled and the middle section stayed is it was.

Hence i had enough and decided to try 9.04, i just hope this works ok.

Thanks to you all, for your replies.

---

### Post by random turnip on 2009-10-16
> **Zundap said:**
> Can anyone please help, i have installed UBUNTU, but i am unable to view youtube, i get an error message saying that i require flashplayer, that downloads no problem, but when i try to install it, i get asked for a password.

I have tried the password that i used to install UBUNTU, and not is not the correct password, could anyone tell me how i find what the password is?

Thanks

When you created your account, the one you probably type in every time you boot your computer or whenever you change any settings, should be the same one.

---

### Post by Zundap on 2009-11-16
Here i go again, i had to reinstall BUNTU, because update screwed up the O'S again?

So i reinstalled UBUNTU and i have the same problem again, i cant instill Adobe flash player to use Youtube.


I have tried nhasians advice re typing the text in to terminal, but is still asking for a password and wont accept "sudo" or "[sudo]" as a password.

I really dont think that my O'S is 64 bit, but how can i tell?



I have typed in to terminal, as advised by carlee, and still nothing happens.
> 2.6.28-11-generic
allen@allen-desktop:~$ 
allen@allen-desktop:~$ 
Any help would be gratefully received, Thanks

---

### Post by Zundap on 2009-11-16
Here i go again, i had to reinstall BUNTU, because update screwed up the O'S again?

So i reinstalled UBUNTU and i have the same problem again, i cant instill Adobe flash player to use Youtube.


I have tried nhasians advice re typing the text in to terminal, but is still asking for a password and wont accept "sudo" or "[sudo]" as a password.

I really dont think that my O'S is 64 bit, but how can i tell?



I have typed in to terminal, but i get the message below
> 2.6.28-11-generic
allen@allen-desktop:~$ 
allen@allen-desktop:~$ 


Any help would be gratefully received, Thanks

---

### Post by oldos2er on 2009-11-16
> **Zundap said:**
> So i reinstalled UBUNTU and i have the same problem again, i cant instill Adobe flash player to use Youtube.

I have tried nhasians advice re typing the text in to terminal, but is still asking for a password and wont accept "sudo" or "[sudo]" as a password.

I really dont think that my O'S is 64 bit, but how can i tell?

I have typed in to terminal, as advised by carlee, and still nothing happens.
Any help would be gratefully received, Thanks

 I hope your password isn't actually "sudo"! Assuming it's not, and you entered **sudo apt-get install ubuntu-restricted-extras** in the terminal, type in the password you chose when you installed Ubuntu. Nothing will be echoed back to the terminal, which is normal.

---

### Post by Zundap on 2009-11-16
Thanks for the reply oldos2er, but i did not type in any password when i installed UBUNTU, i was never given the option to do so.

i typed in to terminal as below, as edvised by nhasain.

sudo apt-get install ubuntu-restricted-extras
Was that not  the right the thing to do?

Any other ideas would be most welcome, i really want to switch over to UBUNTU, but its not much good to me as it is.

---

### Post by Swatfoot on 2009-11-16
I cant help you with password other that check your numberlock but I suggest following this [http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by Zundap on 2009-11-16
OK, Thanks swatfoot

---

### Post by Zundap on 2009-11-16
I have just has a look at the info provided in the link, but it is way too complicated for me to understand i am afraid, i will try to understand it, but if any one else could help in anyway, i will be grateful.

Thanks.

---

### Post by chaanakya_chiraag on 2009-11-16
@Zundap: The sudo password is the one you use to log in.  Have you tried entering that password?  Open up a Terminal (Applications -> Accessories -> Terminal).  Again, use the command ```
sudo apt-get install ubuntu-restricted-extras
``` and enter in your password.  **It will not show you the password as you enter it!  This is normal!  **If this doesn´t work, please post the output.  Thanks!

---

### Post by Zundap on 2009-11-16
Please forgive me if i am being stupid here, i really don't have any experience at all.

Are you saying that i type in this below, then add a password to the end of it?


**sudo apt-get install ubuntu-restricted-extras**

---

### Post by chaanakya_chiraag on 2009-11-16
@Zundap: It´s alright.  I was there once.  No.  What you have to do is press enter after entering the command into the terminal.  When it asks for the sudo password, **then** type in your **login** password.  Cheers!

---

### Post by Zundap on 2009-11-16
Thank schaanakya_chiraag, But i don't have a log in password, i never have had one, when i installed UBUNTU, it never gave me the opportunity to have one.

Thats why i dont understand why i am being asked for one when i try to install programs.

---

### Post by halitech on 2009-11-16
you may have your system set to log in automatically but you *have* to have a password. If you don't remember it, look here for resetting it

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Zundap on 2009-11-16
Thanks halitech, its a bit late for me now, so i will give that a try to-morrow, i will post back the results then.

Thanks again.

---

### Post by chaanakya_chiraag on 2009-11-16
btw, you don´t need to put ubuntu in caps every time :D

---

### Post by Zundap on 2009-11-17
> **chaanakya_chiraag said:**
> btw, you don´t need to put ubuntu in caps every time :D
Ok, i will remember that in future and thanks for all your help. :D

---

### Post by Zundap on 2009-11-17
> **halitech said:**
> you may have your system set to log in automatically but you *have* to have a password. If you don't remember it, look here for resetting it

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Thanks []("http://ubuntuforums.org/member.php?u=69393")halitech that cracked it, i am now youtubing with no problem

I would also like to thank everyone who posted advise in this thread, i did in actual fact learn something from each and every one of you, thanks a million to all of you great guys.  :D

---

### Post by halitech on 2009-11-17
glad to hear you got it working and that you learned something today :)

---

### Post by chaanakya_chiraag on 2009-11-17
@Zundap: Please mark your thread solved by clicking on Thread Tools -> Mark as Solved so that others can learn from your experience.  Thanks!

---

### Post by Zundap on 2010-01-09
Sorry for thedelay, but i have now marked it solved. :D

---

