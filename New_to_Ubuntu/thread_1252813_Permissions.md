---
title: "Permissions"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by old_dope on 2009-08-29
How do i set permissions for the media directory and check that i have DVD codecs installed on my pc. Thanks

---

### Post by halitech on 2009-08-29
are you referring to the /media directory? if so, it should have the proper permissions from the install

for dvd
```
sudo apt-get install xubuntu-restricted-extras libdvdcss2
```should get you going

---

### Post by NoaHall on 2009-08-29
/media is where external storage devices are show once they are mounted. Are you wishing to play a dvd from there?

---

### Post by old_dope on 2009-08-29
When i insert a DVD into the drive Totem Movie Player opens and then the following error message appears:

An error occurred
Could not open location; you might not
have permission to open the file

I have just made sure that libdvdcss2 is installed so surely permissions must be the culprit for the error message appearing?

So could anyone explain how i might set permissions and get to watch my dvd. Thanks in advance

---

### Post by NoaHall on 2009-08-29
What kind of account are you running?

---

### Post by old_dope on 2009-08-29
Do i have to log in as sudo? I am running Xubuntu 8.10

---

### Post by NoaHall on 2009-08-29
You shouldn't have to log in as sudo. Have you tried it since installed the codecs? Try playing it with vlc media player (sudo apt-get install vlc)

---

### Post by old_dope on 2009-08-29
Yes i have tried to play the dvd since installing the codecs but all i get is the error message

---

### Post by NoaHall on 2009-08-29
Maybe you should try updating to jaunty, and see if the problem still exists.

---

### Post by halitech on 2009-08-29
can you open any disk that you put in the dvd player?

can you post the output of
```
groups
```

---

### Post by bodhi.zazen on 2009-08-29
> **old_dope said:**
> Yes i have tried to play the dvd since installing the codecs but all i get is the error message

What error message ?

---

### Post by old_dope on 2009-08-29
Don't know if i'm doing this right but here goes!
I opened a terminal and typed: groups. And the output was:

old_dope@old_dope-desktop:~$ groups
old_dope adm dialout cdrom plugdev lpadmin sambashare
old_dope@old_dope:~$

The error message i get when i try to play a dvd is:

An error occurred
Could not open location;you might not
have permission to open the file

---

### Post by halitech on 2009-08-29
looks like its a problem where you don't belong to all the groups needed

here is mine
```
daryl@debian:~$ groups
daryl dialout cdrom floppy audio video vboxusers
daryl@debian:~$
```

You are missing the audio, video and plugdev groups which could be why it won't play

```
 sudo usermod -G <group ids here> <user name here>
```is the syntax so you would do
```
sudo usermod -G audio video old_dope
```
you may need to reboot for the changes to take effect

---

### Post by bodhi.zazen on 2009-08-29
> **halitech said:**
> you may need to reboot for the changes to take effect

you [s]may[/s] will almost certainly need to reboot for the changes to take effect.

The changes will take effect if you open a new shell (terminal) in the new shell, but your session was started with the old groups, and thus needs to be re-stated.

---

### Post by halitech on 2009-08-29
> **bodhi.zazen said:**
> you [s]may[/s] will almost certainly need to reboot for the changes to take effect.

The changes will take effect if you open a new shell (terminal) in the new shell, but your session was started with the old groups, and thus needs to be re-stated.

Thanks bodhi, I wasn't 100percent sure if the reboot was needed as I've only added myself to vbox and that was awhile ago. Any other reason you can think of that the OP can't play dvds with the error they are getting?

---

### Post by bodhi.zazen on 2009-08-29
encrypted DVD ? Some players work better then others ?

I do not use the DVD much on the computer, I watch DVD on the big screen.

My guess is perhaps with hal, and problems with hal are one reason to reboot (restartign hal does not always work).

Of course that is a blind guess in the dark.

---

### Post by halitech on 2009-08-29
never thought of the dvd being encrypted, good possibility, especially if store bought

I don't either, usually I burn things and watch them on the tv as well

I guess until the OP comes back we are all sitting in the dark wondering.

---

### Post by oboedad55 on 2009-08-29
> **halitech said:**
> never thought of the dvd being encrypted, good possibility, especially if store bought

I don't either, usually I burn things and watch them on the tv as well

I guess until the OP comes back we are all sitting in the dark wondering.

I get this same error with movie player with several different versions of Ubuntu. VLC, however, works just fine.

--Jon

---

