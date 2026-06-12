---
title: "Remove &quot;Unlock Keyring&quot; on start-up"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by Nebelhom on 2010-03-04
hi guys,

I'm being daft. Since recently, on start-up of ubuntu there is always a pop-up windows asking to unlock key (like when you go into System -> Administration - Users and Groups and you want to change a parameter).

It is a nuisance more than anything, but it is doing my head in. How can I stop it from doing that?

thanks for the feed back.

---

### Post by kanikilu on 2010-03-04
Do you have Ubuntu set up to login automatically? If so, I think this may be causing the "unlock keyring" prompt on start up...

---

### Post by wojox on 2010-03-04
1) Right-click on the Network Manager applet and select "Edit Connections"
2) Click on the Wireless tab, make sure your wireless network is selected, and click on "Edit".
3) At the bottom on the new window, check "Available to all users".
4) Close all the windows, reboot, and test to ensure that this solves the issue.

---

### Post by Nebelhom on 2010-03-04
@ wojox:

I don't have wireless. Still on old fashioned cable connection, but I had a look anyways. "Available to all users" is ticked, so it isn't that, but it is interesting you mention that, because on start-up as well, my pdigin/empathy messenger gives a "connection error" but then logs in fine. I didn't think there was a connection between the two issues...


@ kanikilu

> Do you have Ubuntu set up to login automatically?

logged into what? I am not sure what you mean... Sorry if this is a very obvious thing that I am asking here...

---

### Post by kanikilu on 2010-03-04
> **Nebelhom said:**
> logged into what? I am not sure what you mean... Sorry if this is a very obvious thing that I am asking here... To the OS - do you have to enter your password on booting up, or is it set to automatically login for you?

---

### Post by Nebelhom on 2010-03-04
Aaaahhh, sorry for that.

On boot up, I am asked for my password. then it goes into the gui and in there the unlock key bit comes up.

Is that what you meant?

---

### Post by kanikilu on 2010-03-04
Yes, that's what I was wondering.

Hmm...if you are logging in, it should automatically unlock the keyring.

Is it possible for you to take a screenshot of the dialog box and attach it here so we might be able to see what's asking for the password? As the wojox suggested, a usual suspect is the Network Manager applet (nm-applet).

A quick search suggest removing/deleting the default keyring (~/.gnome2/keyrings/default.keyring), but maybe moving it to another location temporarily would be safer while testing to see if that works...

---

### Post by spiderbatdad on 2010-03-04
I believe the problem  may have began as the result of changing your user password.
If this is the case launch seahorse and go to the passwords tab. right click on the word login and select change password...change to match user password.

---

### Post by crlang13 on 2010-03-04
> **spiderbatdad said:**
> I believe the problem  may have began as the result of changing your user password.
If this is the case launch seahorse and go to the passwords tab. right click on the word login and select change password...change to match user password.

If you go to applications > accessories > password and encryption keys, you'll see all your stored passwords thrown onto your default keyring.  If you right click on this, you can change the password for your default keyring.  If you change it to be nothing, you'll get a warning saying that it leaves your passwords unsecure, say ok.  This gives auto access to your default keyring to the apps that use it.  That should be fine for network passwords and things you're not concerned about.

If there are passwords you're concerned about, create a 2nd keyring with a password on it.:P

---

### Post by Nebelhom on 2010-03-04
@ crlang13 and spiderbatdad

Yep, that did it. awesome! For the sake of udnerstanding ubuntu better, can you guys explain to me why it did that in the first place?

cheers to all you guys for helping out.

---

### Post by spiderbatdad on 2010-03-04
> **Nebelhom said:**
> @ crlang13 and spiderbatdad

Yep, that did it. awesome! For the sake of udnerstanding ubuntu better, can you guys explain to me why it did that in the first place?

cheers to all you guys for helping out.

Either you changed your user password after creating the keyring or used a different password when creating the keyring.

---

### Post by Domitella on 2011-06-04
I'm having this problem too, and none of the fixes here seem to fix it! 

It's only started happening recently, and I haven't changed any of my passwords at all, so that can't be the problem.

It's SO annoying!

---

### Post by el_koraco on 2011-06-04
> **Domitella said:**
> I'm having this problem too, and none of the fixes here seem to fix it! 

It's only started happening recently, and I haven't changed any of my passwords at all, so that can't be the problem.

It's SO annoying!

Just don't do the automatic logion thing, that's asking for trouble. Other than that, go to "Passwords and Encryption Keys", right click on "login" and/or default password, click change, enter your login password, and leave the rest of the fields blank. You'll get a prompt asking "do you want to use unsafe storage", select yes.

---

### Post by Domitella on 2011-06-06
> **el_koraco said:**
> Just don't do the automatic logion thing, that's asking for trouble. Other than that, go to "Passwords and Encryption Keys", right click on "login" and/or default password, click change, enter your login password, and leave the rest of the fields blank. You'll get a prompt asking "do you want to use unsafe storage", select yes.

Ack, thanks but that didn't work for me.

But I found [this in the comments here]("http://johnny.chadda.se/article/unlock-the-gnome-keyring-upon-login/"), which did:

> I appreciate that this may not be the right way to go about it but I have managed to get this to work for me.


 I currently have Ubuntu running on an old computer which I use as a  file-server, ftp -server, http intranet server and fuppes media server.   I was set to auto login and run fuppes on startup so that all I had to  do was switch on and everything worked.  I would use VNC to control the  server and did not need a keyboard or screen attached to the server. 



 I recently upgraded to 10.04 Lucid and found I had the annoying  problem that it would not connect to the network without putting in my  password again to unlock the key-ring which meant that I could not use  VNC to control the server.  I tried different methods including setting  the keyring password to nul (blank) and playing with “sudo apt-get  install libpam-keyring” but without any success.  So in desperation, I  stopped the keyring apps from starting in the first place.


 System|Preferences|Startup Applications:
 

unticked the following:
Bluetooth Manager – Don’t need it, not running anything bluetooth.
Certificate and Key Storage.
Secret Storage Service..
Ubuntu One – Don’t need it
Visual Assistance – Don’t need it.
 

Now, it runs and connects without issue or password request.  Just  tested ftp and that works fine too.  Http working fine.  Shared  directories are fine.  Now I just need to get my fuppes to run on  startup and I’ll be happy.
 If you need to use “Certificate and Key Storage” and “Secret Storage  Service” then this probably won’t help you but I think it would indicate  that there is a problem either with these services or the way they  communicate with other services.  I confess to being a complete Ubuntu  noob but I hope this points people in the right direction.
I suspect Ubuntu One may have been the culprit in my case.

---

