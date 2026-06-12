---
title: "How can I change permissions so I can copy a folder?"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by thejiggler on 2011-05-14
I'm completely new to Ubuntu and Terminal so please excuse the naivity of any questions.

I'm  trying to recover a folder and it's contents from a pc that crashed.  The pc was running on Windows XP and I had to enter a password to log on  as administrator. I've booted up this pc using ubuntu 10.10 as a live  CD and copied the majority of the files and folders I want onto a memory  stick but cannot copy over a certain folder. This folder was "hidden"  in my previous set-up.

I tried using the Terminal to copy the  files to the USB stick. After reading some posts to this forum I tried  the following command:

sudo cp -R <filename> <destination location>

Each file is then listed with"Permission denied" next to it.

Is there any way I could change the permissions on this folder and its contents to allow myself to copy to a memory stick?
Cheers

---

### Post by Drenriza on 2011-05-14
navigate to the folder on the usb stick, with the terminal.

try use sudo chmod 777 (just give all read, write and execute privileges.) and then try copy the folder

sudo scp -r source/ /destination/

---

### Post by rvchari on 2011-05-14
[QUOTE=thejiggler;10814515]I'm completely new to Ubuntu and Terminal so please excuse the naivity of any questions.

I'm  trying to recover a folder and it's contents from a pc that crashed.  The pc was running on Windows XP and I had to enter a password to log on  as administrator. I've booted up this pc using ubuntu 10.10 as a live  CD and copied the majority of the files and folders I want onto a memory  stick but cannot copy over a certain folder. This folder was "hidden"  in my previous set-up.

I tried using the Terminal to copy the  files to the USB stick. After reading some posts to this forum I tried  the following command:

sudo cp -R <filename> <destination location>

Each file is then listed with"Permission denied" next to it.

Is there any way I could change the permissions on this folder and its contents to allow myself to copy to a memory stick?
Cheers[/QUOTE

i ll tell u an easy way to do the easier copy/paste in nautilus.
hit Alt+F2 and type gksu nautilus /home/YOUR USERNAME
u ll open a nautilus window with admin previleges. wthin that window you can navigate to any file and do copy and paste. note that the user previleges r root previleges and you may not be able to access or read without it.

still your copy paste wil be easier]

---

### Post by ClientAlive on 2011-05-14
> **rvchari said:**
> [QUOTE=thejiggler;10814515]I'm completely new to Ubuntu and Terminal so please excuse the naivity of any questions.

I'm  trying to recover a folder and it's contents from a pc that crashed.  The pc was running on Windows XP and I had to enter a password to log on  as administrator. I've booted up this pc using ubuntu 10.10 as a live  CD and copied the majority of the files and folders I want onto a memory  stick but cannot copy over a certain folder. This folder was "hidden"  in my previous set-up.

I tried using the Terminal to copy the  files to the USB stick. After reading some posts to this forum I tried  the following command:

sudo cp -R <filename> <destination location>

Each file is then listed with"Permission denied" next to it.

Is there any way I could change the permissions on this folder and its contents to allow myself to copy to a memory stick?
Cheers[/QUOTE

i ll tell u an easy way to do the easier copy/paste in nautilus.
hit Alt+F2 and type gksu nautilus /home/YOUR USERNAME
u ll open a nautilus window with admin previleges. wthin that window you can navigate to any file and do copy and paste. note that the user previleges r root previleges and you may not be able to access or read without it.

still your copy paste wil be easier]


If it still gives you grief about copying the thing you can log in as the superuser (in the terminal) and probably accomplish the task. Since you are running live I don't think you can hurt anything that is part of the live cd anyway.

Navigate to the folder you want through the terminal using the "cd" command. Once you are there you can log in as the super user by entering the following:

```
sudo -s
```

It will ask you for your password. Enter it and press enter.

Now, with this permission level, I think you could copy your folder using the cp command. Make sure that where you are copying it to does not have another folder with the same name as the cp command will just overwrite the other one. You can avoid any potential problems by adding the verbose option to the command. It looks like this:

```
cp -rv foldername
```

In the above example "cp" is the command; then a space; then we put a dash to indicate we're going to add an option (in this case two options); the "r" is "recursive" so it will copy the entire contents of the folder; the "v" is "verbose" so it will give you feedback on the operation before it exacutes it.

HTH

---

### Post by thejiggler on 2011-05-14
> **Drenriza said:**
> navigate to the folder on the usb stick, with the terminal.

try use sudo chmod 777 (just give all read, write and execute privileges.) and then try copy the folder

sudo scp -r source/ /destination/

Can't nagvigate to the USB stick. Says

bash: cd: PNY Lovely/:Pemission denied

Should I be navigating to the USB stick anyway to perform this command? The USB stick is the destination for the folder. Any more ideas. Cheers

---

### Post by thejiggler on 2011-05-14
> **rvchari said:**
> [QUOTE=thejiggler;10814515]I'm completely new to Ubuntu and Terminal so please excuse the naivity of any questions.

I'm  trying to recover a folder and it's contents from a pc that crashed.  The pc was running on Windows XP and I had to enter a password to log on  as administrator. I've booted up this pc using ubuntu 10.10 as a live  CD and copied the majority of the files and folders I want onto a memory  stick but cannot copy over a certain folder. This folder was "hidden"  in my previous set-up.

I tried using the Terminal to copy the  files to the USB stick. After reading some posts to this forum I tried  the following command:

sudo cp -R <filename> <destination location>

Each file is then listed with"Permission denied" next to it.

Is there any way I could change the permissions on this folder and its contents to allow myself to copy to a memory stick?
Cheers[/QUOTE

i ll tell u an easy way to do the easier copy/paste in nautilus.
hit Alt+F2 and type gksu nautilus /home/YOUR USERNAME
u ll open a nautilus window with admin previleges. wthin that window you can navigate to any file and do copy and paste. note that the user previleges r root previleges and you may not be able to access or read without it.

still your copy paste wil be easier]

Tried this. Considering Im using a live CD what would my username be? I tried the usename Ubuntu. This username works if the computer logs me out after a period of inactivity.

---

### Post by ClientAlive on 2011-05-14
> **thejiggler said:**
> [QUOTE=rvchari;10814556]

Tried this. Considering Im using a live CD what would my username be? I tried the usename Ubuntu. This username works if the computer logs me out after a period of inactivity.

You can discover the username and hostname (or computer name) by typing "id" into the terminal and hit enter. The format is "username@hostname".

> 
Is there any way I could change the permissions on this folder and its contents to allow myself to copy to a memory stick?
 Cheers

With a file on a Linux system - sometimes using the sudo command or logging in as sudo using

```
sudo -s
```

will give you the permission you need to carry out the operation. Since you are talking about a folder on a microsoft partition (aren't you?) I'm not sure if it is applicable or not.

---

### Post by dcsoldschool53 on 2011-05-14
> **thejiggler said:**
> Can't nagvigate to the USB stick. Says

bash: cd: PNY Lovely/:Pemission denied

Should I be navigating to the USB stick anyway to perform this command? The USB stick is the destination for the folder. Any more ideas. Cheers

Try using this to navigate to your USB```
/media/PNY\ Lovely/
```That is, if your USB stick is called PNY Lovely. There is a space between the \ and Lovely.

---

### Post by thejiggler on 2011-05-16
```
sudo -s
```will give you the permission you need to carry out the operation. Since you are talking about a folder on a microsoft partition (aren't you?) I'm not sure if it is applicable or not.[/QUOTE]
 
Typed in id and it came up with several differnt option but none in the format something@somthing. I tried them anyway and each time I recieved the error message "Could not find "/home/whatever". When I first open up terminal it reads ubuntu@ubuntu: So I tried this and the same error message appeared.

Yeah this is on a Microsoft partition - Anyone got anymore ideas? I'm getting desperate.

---

### Post by ClientAlive on 2011-05-17
> > **thejiggler said:**
> ```
sudo -s
```will give you the permission you need to carry out the operation. Since you are talking about a folder on a microsoft partition (aren't you?) I'm not sure if it is applicable or not.
 
Typed in id and it came up with several differnt option but none in the format something@somthing. I tried them anyway and each time I recieved the error message "Could not find "/home/whatever". When I first open up terminal it reads ubuntu@ubuntu: So I tried this and the same error message appeared.

Yeah this is on a Microsoft partition - Anyone got anymore ideas? I'm getting desperate.


I must have really been tired when I wrote that. Now that I read it again it sounds crazy.

The "username" and "host" (aka the computer name) are what is shown in the terminal before the cursor.

Here is what mine looks like:

```
shine@lineNine:~$
```

The part before the @ sign is my user name, the part after the @ sign is my host name (or the computer's name, the tilde (~) represents your home directory but the place it is located in the line of information is what tells you your location, the $ is just the end of the line and then the cursor. So, for instance, if I change directory to another location that piece of information will change to reflect the directory I am in. Like so:

```

shine@lineNine:**~**$ cd Documents
shine@lineNine:~/**Documents**$

```

Compare bolded and notice they both just precede the $ sign.


Also, I should have been clearer about this. Everything I have talked about has to do with things on a Linux system. How these things may or may not apply to folders on a Windows system I don't know. I offered the information to give you some fuel to go on to experiment with. How the permissions work with folders on a Linux system - I could explain. Since you're talking about Windows, I'm not certain whether that may be of any use to you though. Especially since changing permissions on things can lead to undesirable consequences (best to be certain about that kind of thing).

You might want to try posting in "Other os/ distro talk"

located here:  [http://ubuntuforums.org/forumdisplay.php?f=401](http://ubuntuforums.org/forumdisplay.php?f=401)

You might stand a better chance of catching someone with more Windows familiarity.

Hope that helps and sorry for the retarded post before.

:)

---

### Post by ClientAlive on 2011-05-17
By the way, I noticed it doesn't look like you added any tags to your thread here. Adding tags can help others find your post to respond to it. When you start a thread, there is a tags field below the window you type the message/ post into. You can type whatever you choose into that field (up to a certain number of characters per tag) and up to five tags separated by commas. I have noticed that when I choose good tags that are closely tied to what my post is about I seem to get more responses and faster too. Maybe it's all in my head though.  :D

Just thought it was worth mentioning.

---

