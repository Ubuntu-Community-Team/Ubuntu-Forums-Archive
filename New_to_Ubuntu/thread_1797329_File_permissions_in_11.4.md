---
title: "File permissions in 11.4"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by critanime on 2011-07-04
Hi
 
I am a complete novice when it comes to Linux. So if I sound a little shaky on explaining something it's because i don't know how to describe it lol. ;)
 
I have been using 11.4 for a few days now and I am loving it. Been a Mac person i settled into the OS with a great amount of ease. however I ran into a snag today and I am unclear as to what to do. 
 
I downloaded Vice from the software centre and it failed to load. However after reading a guide I discovered i needed to copy some things over from the original source. I downloaded the source corresponding to my version, which I found from running the app through terminal, but I can't seem to copy the required files from the source file into the correct folder. I keep getting an error saying I don't have permission to copy the files into the destination folder. 
 
When I tried to change permissions on the folder it just didn't seem to do anything. So I am confused on what I need to so to change permissions of a file or folder. 
 
A friend mentioned using as SU or SUDO command. Or logging in using the root password I setup and changing the permissions that way. However I recall never setting a root password. Also when I try SU it asks me for a password which I don't know. 
 
please help :(
 
Just a little extra info. My friend has never used Ubuntu so he is unclear as to what to do as he mainly deals in command line stuff with linux.

---

### Post by dFlyer on 2011-07-04
> **critanime said:**
> Hi
 
I am a complete novice when it comes to Linux. So if I sound a little shaky on explaining something it's because i don't know how to describe it lol. ;)
 
I have been using 11.4 for a few days now and I am loving it. Been a Mac person i settled into the OS with a great amount of ease. however I ran into a snag today and I am unclear as to what to do. 
 
I downloaded Vice from the software centre and it failed to load. However after reading a guide I discovered i needed to copy some things over from the original source. I downloaded the source corresponding to my version, which I found from running the app through terminal, but I can't seem to copy the required files from the source file into the correct folder. I keep getting an error saying I don't have permission to copy the files into the destination folder. 
 
When I tried to change permissions on the folder it just didn't seem to do anything. So I am confused on what I need to so to change permissions of a file or folder. 
 
A friend mentioned using as SU or SUDO command. Or logging in using the root password I setup and changing the permissions that way. However I recall never setting a root password. Also when I try SU it asks me for a password which I don't know. 
 
please help :(
 
Just a little extra info. My friend has never used Ubuntu so he is unclear as to what to do as he mainly deals in command line stuff with linux.

Is this a .deb, .bin or .tar.gz file?

---

### Post by critanime on 2011-07-04
.tar.gz file which I tried to copy from first, the extracted to the desktop when that failed and then to a folder in my home directory when that failed.

---

### Post by critanime on 2011-07-05
After doing some reading in the ubuntu docs I have come across this command.

```
Sudo chown
```

Am I hitting the right path with this command? As the docs have just sent my head spinning lol :-k

---

### Post by rosencrantz on 2011-07-05
OK, just a few things to clear up:
1) Ubuntu differs from other Linux distributions by not setting a root password, so the root account is inaccessible by default. You are supposed to do things that require permission with sudo (you have full permissions but basically stay in your user account)
2) did you manage to extract the tar file or did that fail already (not quite clear from your post)? If yes, you might have a corruption problem. Try downloading once more.
3) Is the file a config file and do you have to copy it to somewhere outside your home directory? Don't change folder permissions or ownership in that case, but do sudo cp <file> <destination dir>.

---

### Post by mikewhatever on 2011-07-05
Generally, the command should be as follows:
```
sudo cp /source /destination
```

You shouldn't need to chown stuff just to copy something. The 'sudo' prefix makes sure that the command is executed with admin privileges.

Edit:
To copy something graphically, launch the file browser with the **gksudo nautilus** command. Create a launcher for it if you want to.
[http://www.psychocats.net/ubuntucat/rootlauncher/](http://www.psychocats.net/ubuntucat/rootlauncher/)

---

### Post by rosencrantz on 2011-07-05
I just read up on vice - it could be that you don't even need to put system files outside your home directory, if that's what you are doing.
According to [http://www.viceteam.org/vice_4.html#SEC24](http://www.viceteam.org/vice_4.html#SEC24)
$HOME/.vice/ might also be an acceptable location.

---

### Post by critanime on 2011-07-05
Thanks for the advice guys. 
 
Just to clarify that tar extracted without any issues. the issues came when I tried to copy the extracted files into the destination folder, which was located in the main vice folder. 
 
I have just done the sudo cp command and that has worked a treat. So now I have the files needed to get the emulator working in the correct places. 
 
So that keeps me happy :D YAY!
 
just out of interested, as I am new to linux, when should I use commands like chmod and chown?

---

### Post by ajaybhat999 on 2011-07-05
chmod command is used to change the permissions of the file..i.e read/write and execute(rwx) permissions..

chown command is to change the owner or the group owner of the file..


type in 'ls -l' in the terminal to view the permissions and owners(both owner and group owner) of the files..

---

