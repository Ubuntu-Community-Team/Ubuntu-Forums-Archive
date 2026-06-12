---
title: "Wireless stopped working for no reason"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by RealG187 on 2009-02-10
When I resumed my computer it said the network manager wanted to access the default keyring, I typed my password and it said it again, I finally clicked deny and restarted my computer (fresh restart) and now I can't connect to my wireless.

I have [Atheros AR5007]("http://ubuntuforums.org/showthread.php?t=766529&page=19") and got it working.

Now it's not working...

---

### Post by cmnorton on 2009-02-11
Start here for your keyring woes. 

[http://ubuntuforums.org/showthread.php?t=1057643](http://ubuntuforums.org/showthread.php?t=1057643)

---

### Post by RealG187 on 2009-02-13
I removed the key from the keyring but my wireless doesn't show up, how do I make it show up, this is really pissing me off.

I think I figured it out. I deleted "madwifi-hal-0.10.5.6-r3875-20081105" I thought once I ran the "make" and "make install" commands from there it would install it self to a system directory and the files there wouldn't be needed (I was cleaning up my home folder). Can I make the "madwifi-hal-0.10.5.6-r3875-20081105" folder hidden so it's like it's not there (not in my way) but still is there, like all those folders in my home folder (like .whatever, example .wine). How can I make .wine not hidden? I guess I could just make a symlink to it (that's not hidden)....

---

### Post by mcduck on 2009-02-13
For the original network problem the solution would have been resetting the keyring password and adding "NetworkManager Applet" and "nm-connection-editor" as allowed applications for the network key (in Seahorse).

Anyway, to hide the "madwifi-hal-0.10.5.6-r3875-20081105" directory you can create a text file called ".hidden" in the same directory, and then add "madwifi-hal-0.10.5.6-r3875-20081105" (without quotes) to that file. .hidden file can be used to hide any directories and files without having to change their name, although it only affects graphical file managers.

For the .wine directory symlinking is the way to go, just like you guessed.

---

### Post by RealG187 on 2009-02-13
so the .hidden file is a text file that lists files to be hiiden.

I notice Ubuntu hides files by their names. a folder called ".something" is a hidden folder called "something".

Also a backup file of t.txt named t.txt~

---

### Post by Narvinye on 2009-04-18
Yes a . at the beginning of a file or directory name makes it hidden.  You can view all files in terminal for the current dir using 'ls -a'.  You can also have periods in your file name as this is not seen as an extension.  :)

I have an atheros card as well and I ran into this same issue after changing my password.  I'm going to try adding my keyring password to seahorse to see if this solves the prompt.  I changed to logging in manually when I started getting this and that took care of it but it still seems buggy.  I'm downloading the RC of 9.04 to see if this is any different.

---

### Post by Narvinye on 2009-04-18
@MCDuck  

I'm not seeing anything in Passwords and Encryptions (seahorse) that is letting me add trusted applications to my rings.  I can add a password and give it a name though so thats what I did.  I'm not seeing where these are being written.

In .gnome2/keyrings the file Applet.keyring is empty and nm-connection-editor.keyring would not open in gedit due to encoding.  When I ran kate on the same file it opens to garbage.  

Do you know where the keyring writes to and how network manager can use this without prompting the user?

---

### Post by RealG187 on 2009-04-20
> **Narvinye said:**
> You can also have periods in your file name as this is not seen as an extension.  :)

I think Ubuntu sorta reads extensions.


For example I make a text file with no extendion. It shows as a text file, I rename it to .mp3 and it shows the icon for mp3.

Also if I take an MP3 with .mp3 or no extension MP3 is shown. If I rename it to txt the text icon is shown. If I remove that extension or change it back to MP3 then mp3 icon shows up.

---

