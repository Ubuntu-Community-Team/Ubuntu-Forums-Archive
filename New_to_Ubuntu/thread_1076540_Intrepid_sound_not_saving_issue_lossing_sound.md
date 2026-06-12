---
title: "Intrepid sound not saving issue lossing sound"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by forestwalkerjoe on 2009-02-21
THIS is my repost to this thread because i was told it would be best for me to post in beginner and get help with it. 
The largest problem is the sound system , which was working.. got messed up.. now that i can get the sounds back on.. the settings wont save for when i reboot. i really need to have help finding a way to Save these working settings so they dont reset each time i have to reboot or log out. 
sorry that there is info in here not completely relevant to my request. There is a link to the Pulse Audio solve that i used and it did work just fine.. and still does if i can get pulse audio to stop trying to connect to a server.. or losing its settings for a default set. 
------------------------------------------------------------------------------------------------------------------------


> **unutbu said:**
> Hi forestwalkerjoe, I am happy to try to help you with the audio problem, but I am not really that knowledgable about fixing sound issues.




<<<<>>>>    Can you explain in more detail what you have tried? 


---------------------------------------------------------------------------------------------------------------------------
I am not good at describing exactly what i am doing.. but i will try. 
Ok.. bare with my lack of good terms here. I will tell you what i DO know works.. and see if you can help me KEEP it that way. 
My system is affected by the sound system glitch in 810 Intrepid. 
the only Solve i was able to get to work.. is the pulse audio fix. 
i had to Go to sounds.. set all sound playback stuff to Detect and the capture to pulse audio. the hardware default was Dell sound blaster (ALSA). then i had to open the Pulse audio Device chooser in APPS AUDIO/video.. and make sure it is running. I see it in the tray above near the Netconnection and volume area. so far.. if it connects.. there is no sound at all. except system sounds when i log in. 
BUT.. if i turn that off.. it asks for a connection.. gives a address.. which i learned i could errase.. but the sounds work. Even the Flash player sounds..which has been a problem for many in this version of Ubuntu. OH.. if i click on the icon that is for pulse audio .. it has a pull down.. default server, sink and source. i have to set the first one to OTHER.. default will not work. each of the other two must be on default. Then i need to open the manager.. and say disconnect. poof i have sound. BUT once i reboot.. the applet for PULSE AUDIO doesnt load.. and IF by some chance it does.. it reverts to its own defaults. It connects to some sort of server.. which overrides the sound properties that DO work. i have to Hit manager.. disconnect.. also HIT Default server area and choose other.. and so forth.. then it comes back. I have no idea how to Save these settings that work.. so they continue to work. Before i messed these up.. Today.. these were not working after the install.. i spent 8 or more hours a day for 3 days trying to fix them. and this link i will put in here.. was the [final solve]("http://ubuntuforums.org/showthread.php?t=789578"). I have retried this and its not changing anything this time. 



Do you believe sound was lost because of the renaming of .gconf and .gnome2? Or was it something else which caused the problem?

------------------------------------------------------------------------------------------------------------------
NO. i was hunting for the answer and messing with settings that seemed to make sense.. before i found your Help. 
--------------------------------------------------------------------

Which version of Ubuntu are you using? Hardy? Intrepid?
---------------------------------------------------------
810 Intrepid off disk i bought from Ebay. 

Please post the output of 
```

ls -ld   .gnome2   .gconf
```
This will allow us to check that the permissions are set correctly, at least at the top level.
-------------------------------------------------------------------------------

OUTPUT:
rj@ubuntu:~$ ls -ld   .gnome2   .gconf
drwx------ 5 rj rj 4096 2009-02-20 23:15 .gconf
drwx------ 8 rj rj 4096 2009-02-20 23:15 .gnome2
rj@ubuntu:~$ 


Have you tried going to System>Pref>Sound and changing to ALSA (instead of Autodetect, OSS, or PulseAudio Sound Server)? Does sound work on this setting? If so, then reboot and see if it sticks. 

If that does not work, it would be best to start a new thread in the Absolute Beginner Forum with a title that includes the words "Pulse Audio". That way, people more knowledgeable than I will take a look at your problem. Post a note here that you have done so and I'll find the new thread and try to help there.



----------------------------------------------------------------------------------------------------------------
I have already put in a thread or two in the past week or more on this sort of issue.. and got very little help. the link above was the best bet.. i just want to know how to save the settings that do work.. or find out WHY they are reverting to the other defaults on reboot. 
It was not doing that before i did the config thing. BUT the rest of my system is working much better now that we have done that. 
from what i understand.. pulse audio is a must in this version of ubuntu.. and flash has a change in it that requires some things for it to work on the Firefox browser in 810 as well.


FWJ

---

### Post by unutbu on 2009-02-25
If you use the GUI to fix the sound, play a song to test sound is working, log out, and then log back in again (without rebooting), does sound still work?

---

### Post by forestwalkerjoe on 2009-02-25
> **unutbu said:**
> If you use the GUI to fix the sound, play a song to test sound is working, log out, and then log back in again (without rebooting), does sound still work?
the answer is no. 
what seems to be happening is the pulse audio server resets to a default.. it works again if i do the pull down.. chose other and errase the native link it's trying to use. then sound comes back. Just a note i use the roll over of a song on the desk top to test.. and i also click the song itself and open up the player.. it doesn't work unless i do the above fix. IF i reboot all the way.. it resets the settings too. 
is there some thing in here that auto saves settings for sound?  or anything else? is there a place to tell pulse audio to save MY settings as opposed it It's idea of the right settings? 

thanks again for helping. 

FWJ

---

### Post by unutbu on 2009-02-25
Okay, I don't know if this will work, but perhaps it's worth a shot:

Click Places>Home Folder.
If you don't see any so-called hidden dot files -- .gconfd in particular -- press Ctrl-h. 
Rename .gconfd to .gconfd-old
Log out, log back in.
The system should detect that you have no .gconfd folder, and make you a new one. 
Repeat the GUI method of fixing your sound.
Log out and log back in.
Are your sound settings retained?

---

### Post by forestwalkerjoe on 2009-02-25
> **unutbu said:**
> Okay, I don't know if this will work, but perhaps it's worth a shot:

Click Places>Home Folder.
If you don't see any so-called hidden dot files -- .gconfd in particular -- press Ctrl-h. 
Rename .gconfd to .gconfd-old
Log out, log back in.
The system should detect that you have no .gconfd folder, and make you a new one. 
Repeat the GUI method of fixing your sound.
Log out and log back in.
Are your sound settings retained?

Ok.. just tried it.. and did a LOG out LOG IN.. and no.. it doesn't retain. 
I have also noticed that one of my widgets.. a trash can, comes back twice.. not once. not sure if this is a clue but .. had to ask.  I really hope i dont have to back up again.. and reinstall the wubi. I would really like to use my PC for other than problem solving. 

FWJ

---

### Post by unutbu on 2009-02-25
Go to System>Admin>Users and Groups
Click Unlock
Click Add User
Click Properties and the User Privileges tab.
Give the new user the ability to "Administer the system" and any other privileges you wish.

Log out, and log in as the new user.
Does sound work out of the box for the new user?
If it does, try rebooting and see if it still works for the new user.
If everything works for the new user, then I suggest copying your data over to the new user. Be sure not to copy .gconf, .gconfd and .gnome2. 

If this works as I hope, you'll have to redo your GNOME settings once more...

---

### Post by forestwalkerjoe on 2009-02-26
> **unutbu said:**
> Go to System>Admin>Users and Groups
Click Unlock
Click Add User
Click Properties and the User Privileges tab.
Give the new user the ability to "Administer the system" and any other privileges you wish.

Log out, and log in as the new user.
Does sound work out of the box for the new user?
If it does, try rebooting and see if it still works for the new user.
If everything works for the new user, then I suggest copying your data over to the new user. Be sure not to copy .gconf, .gconfd and .gnome2. 

If this works as I hope, you'll have to redo your GNOME settings once more...
well.. i opened up the New User.. and did as you suggested.. when i logged into the new user non of the settings were on by default.. meaning i had no net connection and Sounds were off. 
it took a little bit to get the DSL line running.. and then i pulled a song off my Maxtor exterior drive.. and it didnt play.. i had to set the  Sounds area.. much like i had before.. ALL autodetect except the Hardware.. the sound capture was Pulse Audio.. i then had to open the Pulse audio chooser.. once the icon was in the tray.. i tried a roll over again.. nothing.. then i tried opening the music.. nothing.. i clicked , as before on the icon.. and chose the OTHER part for server.. and then erase the Server address..and i again.. like the RJ user.. had sound.. but sound was On/ off/ ON Off.. On off. which is a new one for me. it sounds like the songs are being played from a radio that you are swinging around your head. TO BE SURE.. if i had a Savable system.. i set it up.. with the exception of the audio sounds in and out.. I had sound.. so i logged in and OUT of the Test User.. and IT did save the Pulse Audio Applet.. and the Net connection.. but again.. the Applet was ON its own default.. just like the Main User.. RJ.. SO .. in a large way.. this Test.. didnt work. 

i have other issues on the RJ User side.. but.. they are not very bad.. just that one sounds issue really. The lap top.. i was able to find the reason for the Black screens at boot up..and find a solve.. till last night..it did an Upgrade.. one that tried to take my system back to the 27-7 Kernel.. when i have been using the 27-12 Kernel.. with a second default in the GRUB of 27-11.. when i rebooted after the DVD upgrade package.. from NON FREE.. it corrupted so bad that i can not log into my system at all. i have been messing with it all morning.. and i FINALLY can get into the system by LIVE CD.. it wasn't even giving me that.. so i am going to have to reach into the systems files by LIVE CD.. to save a couple of things.. and then find out how to whip out the WUBI on lap top again.. and restart the install. 
ONCE i get the Desk top Sounds issue solved.. i am going to be VERY VERY CAREFUL with the DESK TOP.. and once i get the LAP TOP black screen solved and stable.. Same there.. i am getting very worn out of working on these two every day. 

thanks for being such a sport and helping me out. 

FWJ

---

