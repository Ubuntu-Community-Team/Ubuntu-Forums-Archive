---
title: "0% Waiting for Headers?"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by Suzanne42 on 2010-09-14
I get this error when I do an upgrade to Ubuntu 10.04 via the terminal, is there anything I can change bcose right now the terminal is jus waiting at this line, I see no progess.

---

### Post by anewguy on 2010-09-14
Could we have just a little more info?  By upgrade, do you mean you are trying to upgrade from a previous release to 10.04?  What did you do (apparently in terminal)?  Was it something like sudo apt-get upgrade or sudo apt-get update?  Was there anything in particular you were trying to get installed?

Thanks!
Dave ;)

---

### Post by Suzanne42 on 2010-09-14
I currently have Ubuntu 9.10. 1st I updated Ubuntu 9.10 via Update Manager then I tried to upgrade through that but after 3 hrs, an error message popped up saying some packages couldn't be upgraded and an option to stop upgrading. So I decided 2 switch to upgrading via terminal, I gave these commands.

sudo aptitude update
followed by
			 				sudo apt-get upgrade 

This is my result:
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid/main gnome-mahjongg 1:2.30.0-0ubuntu6
  Connection failed
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid/main gnome-sudoku 1:2.30.0-0ubuntu6
  Connection failed
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid/main gnomine 1:2.30.0-0ubuntu6
  Connection failed
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid/universe gnotravex 1:2.30.0-0ubuntu6
  Connection failed
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid/universe gnotski 1:2.30.0-0ubuntu6
  Connection failed
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid/universe gtali 1:2.30.0-0ubuntu6
  Connection failed
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid/universe iagno 1:2.30.0-0ubuntu6
  Connection failed
Get:1 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid/universe laptop-mode-tools 1.52-1ubuntu2 [120kB]
Get:2 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid-updates/main libsdl1.2debian-alsa 1.2.14-4ubuntu1.1 [213kB]
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid/main libsexy2 0.1.11-2build2             
  Connection failed
10% [Waiting for headers]
This is the part where upgrade fails, before this everything was sucessfully upgraded.

---

### Post by Suzanne42 on 2010-09-14
Btw there's nth wrong with my Internet. I am using the same Ubuntu 9.10 to post on this forum. I can access everything online.

---

### Post by da burger on 2010-09-14
Hey, did you have this problem before? How long has it been happening?
 
Looking at the error messages it appears that you can't connect to the server for some reason. If your net connection is fine then I would advise that you try switching servers. If you need help with that then please just post back here.

---

### Post by Suzanne42 on 2010-09-14
Ok, I sucessfully upgraded to Ubuntu 10.04 through the terminal but when I restart the comp, the Ubuntu logo flashes after which I get a black screen.

---

### Post by anewguy on 2010-09-14
When you get the black screen, try the following:

- hold the crtl and alt keys and press the F1 key

- do you get a text-based login screen?

- if so, login using your normal userid and password, then type:
lspci <press enter>

This will output a list of hardware your system knows about that uses the internal PCI bus - this is where normally your video will be.  Search through that output for a line the says something like VGA or graphics controller in it somewhere.  Write down that line, then boot into whatever OS you are using to post here and post that line back here.  There are several possible solutions, but it would be great to have that information.

Dave ;)

---

### Post by Suzanne42 on 2010-09-14
NVIDIA Corporation MCP67 PCI Express Bridge is the line I get. NVIDIA is obviously the graphics card. Now qn is, what do I type next or do I reboot & do something in the BIOS utility setup?

---

### Post by sikander3786 on 2010-09-14
> **Suzanne42 said:**
> NVIDIA Corporation MCP67 PCI Express Bridge is the line I get. NVIDIA is obviously the graphics card. Now qn is, what do I type next or do I reboot & do something in the BIOS utility setup?
Press and hold down the Shift key as soon as your computer gets past the BIOS screen. Grub menu will pop up. Select the top most entry and press "e" to edit it. Using arrow keys navigate to the the words "quiet and splash", delete them and type "nomodeset" in their place. Press Ctrl and X to boot. If the boot was successful, go to System >>> Administration >>> Hardware Drivers and activate the recommended drivers for your card.

If the above solution doesn't work, you might have to delete your xorg.conf file. But first try it and post back.

---

### Post by Suzanne42 on 2010-09-14
Sikander, I din see the "splash & quite" option in the first option of the grub menu. Anyways I chose the sec option(recovery), let's see wat happens.

---

### Post by CharlesA on 2010-09-14
> **Suzanne42 said:**
> Sikander, I din see the "splash & quite" option in the first option of the grub menu. Anyways I chose the sec option(recovery), let's see wat happens.

You need to select the first kernel and hit "e" to edit it. 

It will be after *linux* and before *initrd*

Anyway, both those options are removed for recovery mode so see if it spits back any errors.

---

### Post by anewguy on 2010-09-14
Exactly what I was after by trying to find out your video adapter type.  Indeed, select the grub menu option that would do a normal boot, not a recovery mode, and do the edit as mentioned.  The nomodeset is the key.

Dave ;)

---

### Post by sikander3786 on 2010-09-14
> **anewguy said:**
> Exactly what I was after by trying to find out your video adapter type.  Indeed, select the grub menu option that would do a normal boot, not a recovery mode, and do the edit as mentioned.  The nomodeset is the key.

Dave ;)
I sensed that you were after the same thought so I posted. :-)

---

### Post by Suzanne42 on 2010-09-14
Guys, m back 2 square one with Ubuntu 9.10 installed. I see the only option is 2 try 2 upgrade via Update Manager, the remaining upgrades all give issues but m wondering if I shud try upgrading again since I may again face a blank screen, has any1 tried upgrading via Update Manager? I dun want a long set of issues if I upgrade again. This Ubuntu is really getting on my nerves.

---

### Post by sikander3786 on 2010-09-14
> **Suzanne42 said:**
> Guys, m back 2 square one with Ubuntu 9.10 installed. I see the only option is 2 try 2 upgrade via Update Manager, the remaining upgrades all give issues but m wondering if I shud try upgrading again since I may again face a blank screen, has any1 tried upgrading via Update Manager? I dun want a long set of issues if I upgrade again. This Ubuntu is really getting on my nerves.
How did you manage to get back to Ubuntu 9.10? If it is not a critical type of server, I will advise you to back up your data and do a clean install with Ubuntu Lucid. To be honest, upgrading has never been successful for everyone.

---

### Post by anewguy on 2010-09-14
sikander3786 - I appreciate you've found both of these before I've had time to get back and look ;)

+1 on the clean install.  I seem to remember back when 10.04 first came out that people were having problems trying to upgrade instead of install.  Remember that on an upgrade, there may be old libs, files, config files, etc., left around that can cause problems.  By backing up your data and then doing a normal install, you get rid of those problems (assuming you change to ext4 and in the installation setup you tell it to format the partition).

So, to recap:  back up your data, then INSTALL 10.04, not upgrade.  Then on the boot you'll probably still need to edit the boot line to include nomodeset to have success.  Once you get that far, let us know and we can help you make the change permanent or help you more if it fails.

Please post back with any questions or concerns!

Dave ;)

---

### Post by Suzanne42 on 2010-09-15
Sikander, actually my comp crashed 3 times alr. Recently, I got the help of a frnd & he somehow manages 2 fix it but only successfully installs Ubuntu 9.10. Anyway, I decided nt 2 do an installation of Ubuntu 10.04, my Internet connectivity seems gd right now so betting on a successful upgrade via Update Manager.

---

### Post by sikander3786 on 2010-09-16
> **Suzanne42 said:**
> Sikander, actually my comp crashed 3 times alr. Recently, I got the help of a frnd & he somehow manages 2 fix it but only successfully installs Ubuntu 9.10. Anyway, I decided nt 2 do an installation of Ubuntu 10.04, my Internet connectivity seems gd right now so betting on a successful upgrade via Update Manager.
Ok. I hope the upgrade goes well this time. Please let us know if it was successful.

---

### Post by Suzanne42 on 2010-09-16
Its not successful, tis is really hopeless. Twice it refused to complete, now tis is the third tym m trying 2 upgrade but its stuck @ the 3rd option "Getting New Packages" fetching file 1328 of 1344. Its been showing the same thing 4 an hr now, jus refuses 2 progress. Last tym after 1.5hrs, it gave a message & gave me the option 2 close. There's absolutely nth wrong with my Internet. I stopped all applications hoping Update Manager wld do its job but it refuses to, can't understand why upgrading is such a pain.

---

### Post by sikander3786 on 2010-09-16
I still recommend that you should try to install 10.04.1. The time you've spent in waiting for the upgrade, Lucid Lynx should have installed in that time. May be we are able to get you past the hurdles you are facing in installation of 10.04.1. Whatever decision you make, Good Luck.

---

### Post by Suzanne42 on 2010-09-16
Right now anyway, m working with 9.10, ltr on will try upgrading again. I wldn mind re installation if it was fast or @ least din cum with so many issues.Since right now, I hve a working comp, m nt keen 2 waste tym on gng thru the burden of reinstallation.

---

