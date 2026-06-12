---
title: "SERIOUS problem with launching executable file on desktop"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by magellancraig on 2010-02-14
Hello all,
 
I am having a vary tough time running an installer for x-plane on my new 9.10 64bit installation. I have updated all files, and I have the current linux hardware drivers installed, and the system is running well in every other respect. System is as follows'
 
Gigabte GA-M57SLI-S4 motherboard
AMD Athalon 64 X2 Dual Core 4400+
4GB RAM
WD Raptor 10,000 RPM SATA disk
HP DVD1040 DVD writer
Ubuntu 9.10 karmic, kernel 2.6.31-14-generic
Mesa and openAL installed (needed for x-plane)
GNOME environment
 
I have searched multiple forums, and have tried everything, including 2 reinstalls. but no matter what I do, I get a bash message stating "no such file or directory"
 
I have checked the permissionson both the file and the Desktop folder, logged in as su, ran chmod +x (filename), tried ./ (filename), ./"(filename)", ./'(filename)', and i still get the same error. The file is there, and was downloaded directly from x-planes site, and unzipped in Unbuntu. 
 
I know others have gotten this to work, and I am fairly computer literate, so I am REALLY frustrated.....if anyone can help, please feel free to contact me. I really need to determine if I can get this to work, or if I should scrap Unbuntu...
 
Thanks all.
 
Craig

---

### Post by nmaster on 2010-02-14
what happens if you double click on the file? you might be making a mistake at the terminal, but the GUI is foolproof.  also, what is the name of the file?

---

### Post by mikewhatever on 2010-02-14
Have you downloaded the demo? How about the output of **ls ~/Desktop**?

---

### Post by Greenwidth on 2010-02-14
..

---

### Post by mikewhatever on 2010-02-14
Probably a silly questions, but have you read the installation manual?

[http://wiki.x-plane.com/Linux_Installation_Walkthrough](http://wiki.x-plane.com/Linux_Installation_Walkthrough)

The problem is likely to be incorrect file name or missing dependencies, and the installation file has quite a lot of those.

---

### Post by magellancraig on 2010-02-15
Thank you all for your responses, I will respond to all here.
 
1. The installer file name is "X-Plane DVD Installer Linux". There is no file extension in the name that I can see, but the file properties list it as an executable.
 
2. Double clicking on the file itself does nothing, there is no response.
 
3. I have followed everything suggessted in the Installing Linux wiki that was mentioned. I have looked over the x-plane.org linux forum also.
 
4. Concerning Mike's response:
 "Have you downloaded the demo? How about the output of **ls ~/Desktop**?"
I am not sure of how to answer this. I am new to linux. But, I suppose this is the list command, and if I call up the list, the filename shows up in the list, highlighted in green, as;
 
"X-Plane DVD Installer Linux" (quotes mine)
 
Thanks

---

### Post by Cabs21 on 2010-02-15
are you sure when you are using chmod that you are using the correct path?  Also if you have spaces in you file name you need to put a "\" before each space.

Example
```
 username$:cd pic and vid
```Wrong


```
 username$:cd pic\ and\ vid
```Correct

Where is this "FILE" stored? under / or under /home/username ?

---

### Post by magellancraig on 2010-02-15
The file is located at:
 
[EMAIL="simop1@simop1-desktop:~/Desktop"]simop1@simop1-desktop:~/Desktop[/EMAIL]
 
 
I am not sure about the chmod question. I haven't used chmod on this file.
 
I have tried the / in the filename before, but to no avail.
 
Thanks

---

### Post by Cabs21 on 2010-02-15
> **magellancraig said:**
> I have checked the permissionson both the file and the Desktop folder, logged in as su, ran chmod +x (filename), tried ./ (filename), ./"(filename)", ./'(filename)', and i still get the same error. The file is there, and was downloaded directly from x-planes site, and unzipped in Unbuntu. 
 

You said you used chmod.  Also you said the file is in /Desktop that means you have to be IN that folder to use chmod on the file.

```
simop1@simop1-desktop:~ CD /Desktop
simop1@simop1-desktop:/Desktop~ chmod +x file\ you\ want\ to\ change

```see how I changed directories with CD then used chmod and that I have \ to show spaces
> **magellancraig said:**
> The file is located at:
 
simop1@simop1-desktop:~/Desktop
 
 
I am not sure about the chmod question. I haven't used chmod on this  file.
 
I have tried the / in the filename before, but to no avail.
 
Thanks

remember its not / to show spaces it \ (backslash) 

~/Desktop seems like a root folder.  Why dont you try putting the file in /home/simop1/Desktop instead and give yourself permission to run the file.  Also is this a linux based file or a windows based file.  Does it have a .exe at the end or something similar??

---

### Post by magellancraig on 2010-02-15
Cabs,
 
I don't see any kind of extension on the file, which is kind of strange. I will rerun chmod with the slashes as you detailed, and will let you know how it goes.
 
Craig

---

### Post by magellancraig on 2010-02-15
Cabs,
 
BTW, the file is in home/simops1/Desktop
 
thanks

---

### Post by magellancraig on 2010-02-15
OK,
 
I made sure i was in the Desktop directory, ran chmod +X, then tried;
 
./X-Plane\ DVD\ Installer\ Linux
 
and still got the same error "bash: ./X-Plane DVD InstallerLinux: No such file or directory" This is while I was logged in as su, and all permissions were correct.
 
I would like to try to run some other executable on the desktop, this would let me know if is a file problem, or a Linux/config/ubuntu/??? problem. I am going to fine a file to download and execute. Any suggesstions?
 
Craig

---

### Post by Cabs21 on 2010-02-15
linux does not use file extensions like windows.  There is no need for .exe in linux

---

### Post by Cabs21 on 2010-02-15
> **magellancraig said:**
> OK,
 
I made sure i was in the Desktop directory, ran chmod +X, then tried;
 
./X-Plane\ DVD\ Installer\ Linux
 
and still got the same error "bash: ./X-Plane DVD InstallerLinux: No such file or directory" This is while I was logged in as su, and all permissions were correct.
 
I would like to try to run some other executable on the desktop, this would let me know if is a file problem, or a Linux/config/ubuntu/??? problem. I am going to fine a file to download and execute. Any suggesstions?
 
Craig

while in /Desktop folder type in terminal dir and show me what it displays

---

### Post by Cabs21 on 2010-02-15
Your file is hidden because its already installed i think.  Try typing ```
 CD Desktop
x-plane
```  and see if the program runs.  any folders with a "." in front of it is a hidden file usually in your home folder not desktop and is an application that you can run.

example
in your home folder there is a .firefox folder that contains everything that the user would need to run firefox.  You can type into terminal firefox and it will open firefox you dont need the . or ./ unless it is in the name of the file

---

### Post by magellancraig on 2010-02-15
No luck,
 
if I try to run "X-Palne" or "x-plane", I get a error message "command not found".
 
Also, I am positive the installer file is in Desktop, not home.
 
I even tried renaming the file, same result. And, this is the third file I have downloaded.

---

### Post by Cabs21 on 2010-02-15
ok is this a linux based file? or a windows based file? where did you get it from?

---

### Post by magellancraig on 2010-02-15
this is a linux file. I got it from [http://wiki.x-plane.com/DVD_Installers](http://wiki.x-plane.com/DVD_Installers). it comes as a .zip file

---

### Post by mikewhatever on 2010-02-15
Can you please post the output of the following command:

ls ~/Desktop

Don't login as root or sudo -s or anything like that.

---

### Post by mechro on 2010-02-15
Just checking, but have you followed the installation instructions that mikewhatever linked? Did you install the extra required libraries?

---

### Post by beegary on 2010-02-15
May help:
You can autocomplete the file name using the TAB key in terminal.

So type something like this in terminal:
cd ~/Des **TAB**


you should see the terminal resolve the address of your desktop (if you have 1 user)
Press return

now start typing the name of your file and use tab again:

./X- **TAB**

Press return
Do you get the same error?

Also please copy and paste any commands you run in terminal it will help find the source of the problem

---

### Post by bruno9779 on 2010-02-15
I have downloaded the game and tried to install it.

I always use TAB autocomplete for complex names, so it was recognized, but it stopped because openal is missing.

---

### Post by mechro on 2010-02-15
I got it to work by following the "installation instructions"...

In **Synaptic** search for **libopenal1**. If it's not marked as installed then install it.

I'm 32-bit, you're 64-bit so first try double clicking your Xplane installer and see if it works. If it still doesn't work then...

In Terminal do **gksudo nautilus**. In nautilus navigate to /usr/lib/**libopenal.so.1**. Right-click **libopenal.so.1** and Make Link. Rename the link to **libopenal.so.0**

Try double clicking your Xplane installer again.

---

### Post by skymera on 2010-02-15
Are you running a 64BIT version of Ubuntu by any chance?

---

### Post by magellancraig on 2010-02-16
Hello all,
 
Yes, I had all required libraries installed through the unbuntu package manager. Also the folder and the file had full read, write, and execute permissions. I actually reverted to version 9.04, and everything worked perfectly the first time. So, I am now up and running. I am going to try and update to 9.10 through the Unbuntu updater, and senak up on it, so to speak. If that dosen't work, I will wipe everything, re-install 9.04, and be happy that I am up in Linux.
 
Thanks for the assistance, I will post the results of the upgrade attempt by tomorrow at the latest.
 
Craig

---

### Post by magellancraig on 2010-02-16
> **skymera said:**
> Are you running a 64BIT version of Ubuntu by any chance?
 
 
Yes, I am running the 64bit version.....I changed to 32 bit when I migrated down to 9.04.
 
When I upgrade to 9.10, I will stick with the 32 bit distro, as X-Plane dosen't really take advantage of the 64bit path (other than expanded RAM addressing) anyway.
 
Thanks.
 
Craig

---

