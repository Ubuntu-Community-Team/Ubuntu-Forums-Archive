---
title: "upgrading / reinstalling java"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by Legeril on 2010-12-30
I'm looking to  remove my current version of Java and upgrade to the newest versions of  Java and hopefully any other components like flash etc, can anyone  advise the best way to go about doing this?

In my system > preferences I have sun Java and OpenJDK listed so I',m not even sure what kind of Java I am running right now =/

---

### Post by akand074 on 2010-12-30
Just open the software center or synaptic package manager (from System > Administration) and just search for flash and java (and whatever else) and remove it.

---

### Post by bludgard on 2010-12-30
I removed all Java via Packet Manager and followed this thread/post:[http://ubuntuforums.org/showpost.php?p=10278371&postcount=9](http://ubuntuforums.org/showpost.php?p=10278371&postcount=9)

Works great for me.:D

---

### Post by Legeril on 2010-12-31
Unfortunately I can't visit any google sites as I am living in China, though none of the .bin files from Java.com seem to be relevant to my version of Ubuntu 10.04.

I have been looking around the Package Manager but there is so much stuff on there I don't know where to start, it says I have Sun Java 6 installed but I'm guessing its out of date as Java.com says I need to upgrade and I can't play Minecraft :mad:

---

### Post by bludgard on 2010-12-31
I used the Linux self extracting file from Java website which is a .bin file.(jre6u23-linux-i586.bin).
 
Direct link for X32 bit version:[http://javadl.sun.com/webapps/download/AutoDL?BundleId=43871](http://javadl.sun.com/webapps/download/AutoDL?BundleId=43871)
 
Here are the instructions that worked for me,please follow exactly:
 
**[SIZE=3][COLOR=#000000][SIZE=4][B]HOW-TO FOR 32 BIT UBUNTU**[/SIZE][/COLOR][/SIZE][/B]
 
 
**[SIZE=3][COLOR=#000000][B]Remove the old version**[/COLOR][/SIZE][/B]
 
[SIZE=3][COLOR=#000000]First you'll want to remove the old JRE or openJDK (if you have it). [/COLOR][/SIZE]
 
[SIZE=3][COLOR=#000000]When JRE is installed from the repositories, do it like this:[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#000000]System - Administration - Synaptic Package Manager[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#000000]Query: [COLOR=#0000ff]sun java[/COLOR][/COLOR][/SIZE]
 
[COLOR=#000000][SIZE=3]Tick all installed packages and choose complete removal.[/SIZE][/COLOR]
 
[COLOR=#000000][SIZE=3]When it's installed manually in [COLOR=#0000ff]/opt/java[/COLOR], see the [[COLOR=#0033cc]instruction at the bottom of this column (under the header Removal)[/COLOR]]("http://sites.google.com/site/easylinuxtipsproject/java#TOC-Removal").[/SIZE]
 
[SIZE=3]If you don't have JRE, then you'll probably have openJDK. That one should be completely removed as well. That can also be done with Synaptic Package Manager (query: [COLOR=#0000ff]openjdk[/COLOR]).[/SIZE]
 
 
[/COLOR]
**[SIZE=3][COLOR=#000000][B]Get JRE**[/COLOR][/SIZE][/B]
 
[SIZE=3][COLOR=#000000]Get the right file from the Java website: [[COLOR=#0033cc]http://www.java.com[/COLOR]]("http://www.java.com")[/COLOR][/SIZE][URL="http://www.java.com"]
[/URL]
[COLOR=#000000][SIZE=3]For 32 bit you want ***Linux (self-extracting file)***; the name of this file ends on [/SIZE][/COLOR][SIZE=3][COLOR=#000000][COLOR=#0000ff]i586.bin[/COLOR][/COLOR][/SIZE][SIZE=3][COLOR=#000000]. You don't want*** Linux RPM (self extracting file)***, of which the file name ends on [/COLOR][/SIZE][SIZE=3][COLOR=#000000][COLOR=#0000ff]i586-rpm.bin[COLOR=#000000],[/COLOR][/COLOR][/COLOR][/SIZE][SIZE=3][COLOR=#000000] because RPM is not built for Ubuntu, but for other Linux distro's.[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#000000]***Note:*** Store the file in the folder Downloads. So in [COLOR=#0000ff]/home/YourUserName/Downloads[/COLOR].[/COLOR][/SIZE] [SIZE=3][COLOR=#000000]Firefox puts downloaded files there by default, but not all web browsers do it like that.[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#000000]For example: user John should place the file in[/COLOR][/SIZE][SIZE=3][COLOR=#000000] [COLOR=#0000ff]/home/John/Downloads[/COLOR][COLOR=#000000]. [/COLOR]When in doubt, check it: upper panel of your desktop - Places - Downloads.[/COLOR][/SIZE]
 
[COLOR=#000000][SIZE=3]This is important for the terminal commands that you'll execute later on, because otherwise they won't be correct.[/SIZE][/COLOR]
 
 
 
**[SIZE=3][COLOR=#000000][B]Install JRE (32-bit)**[/COLOR][/SIZE][/B]
 
[SIZE=3][COLOR=#000000]***Note:*** the terminal commands in this how-to possibly refer to an older version of JRE. When there's a newer version, you can simply adapt the file names in the terminal commands.[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#000000]***This how-to has been written for JRE 6 update 23 (32 bit version).***[/COLOR][/SIZE]
 
 
[SIZE=3][COLOR=#000000]1. Go to the folder [COLOR=#0000ff]opt[COLOR=#000000], with the following command:[/COLOR][/COLOR][/COLOR][/SIZE]
 
[COLOR=#000000][SIZE=3]Applications - Accessories - Terminal[/SIZE][/COLOR]
 
[COLOR=#000000][SIZE=3]Type (use copy/paste: rapidly click three times on the blue line, in order to select the entire line).[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3][COLOR=#0000ff]cd /opt[/COLOR][/SIZE]
 
[SIZE=3]Press Enter.[/SIZE]
 
 
[SIZE=3]2. Create a new subfolder, with the following command line. [/SIZE]
[/COLOR][SIZE=3][COLOR=#000000]Type (copy/paste):[/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][COLOR=#0000ff]sudo mkdir java[/COLOR][/COLOR][/SIZE]
 
[COLOR=#000000][SIZE=3]Press Enter.[/SIZE][/COLOR]
 
[COLOR=#000000][SIZE=3]Type your password. You won't see anything, not even dots, this is normal.[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Press Enter.[/SIZE][/COLOR]
 
 
[COLOR=#000000][SIZE=3]3. Go to the new folder, with the following command.[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Type (copy/paste):[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3][COLOR=#0000ff]cd java[/COLOR][/SIZE]
 
[SIZE=3]Press Enter.[/SIZE]
 
 
[SIZE=3]4. Create a new subfolder, with the following command.[/SIZE]
[SIZE=3]Type (copy/paste):[/SIZE]
[SIZE=3][COLOR=#0000ff]sudo mkdir 32[/COLOR][/SIZE]
 
[SIZE=3]Press Enter.[/SIZE]
 
 
[SIZE=3]5. Move the JRE file that you just downloaded, into this newest folder, with the following command.[/SIZE]
[/COLOR][SIZE=3][COLOR=#000000]Type (copy/paste):[/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][COLOR=#0000ff]sudo mv ~/Downloads/jre-6u23-linux-i586.bin /opt/java/32[/COLOR][/COLOR][/SIZE]
 
[COLOR=#000000][SIZE=3]Press Enter.[/SIZE][/COLOR]
 
 
[COLOR=#000000][SIZE=3]6. Make the file executable, with the following command.[/SIZE][/COLOR]
[SIZE=3][COLOR=#000000]Type (copy/paste):[/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][COLOR=#0000ff]sudo chmod 755 /opt/java/32/jre-6u23-linux-i586.bin[/COLOR][/COLOR][/SIZE]
 
[COLOR=#000000][SIZE=3][COLOR=#000000][COLOR=#000000]Press Enter.[/COLOR][/COLOR][/SIZE]
 
[SIZE=3]Now you're going to install JRE, by executing this file.[/SIZE]
 
 
[SIZE=3]7. First, go to the new folder, with the following command.[/SIZE]
[/COLOR][SIZE=3][COLOR=#000000]Type (copy/paste):[/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][COLOR=#0000ff]cd /opt/java/32[/COLOR][/COLOR][/SIZE]
 
[COLOR=#000000][SIZE=3]Press Enter.[/SIZE][/COLOR]
 
 
[COLOR=#000000][SIZE=3]8. Execute the file, with the following command.[/SIZE][/COLOR]
[SIZE=3][COLOR=#000000]Type (copy/paste):[/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][COLOR=#0000ff]sudo ./jre-6u23-linux-i586.bin[/COLOR][/COLOR][/SIZE]
 
[COLOR=#000000][SIZE=3]Press Enter.[/SIZE][/COLOR]
 
[COLOR=#000000][SIZE=3]Now the license agreement appears. [/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Press as many times on the ***space bar***, until you see the following text:[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3][COLOR=#0000ff]Do you agree to the above license terms? [yes or no][/COLOR][/SIZE]
 
[SIZE=3]Type:[/SIZE]
[SIZE=3][COLOR=#0000ff]yes[/COLOR][/SIZE]
 
[SIZE=3]Press Enter.[/SIZE]
 
[SIZE=3]***Note:*** it's possible that you won't see a license agreement. For example because you've already accepted it previously, during the installation of an older version of JRE from the repositories.[/SIZE]
 
 
[/COLOR]
**[SIZE=3][COLOR=#000000][B]Inform the system and make the new JRE the default**[/COLOR][/SIZE][/B]
 
[SIZE=3][COLOR=#000000]9. Now you'll want to tell the system, that there's a new Java version available.[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#000000]Type (copy/paste):[/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][COLOR=#0000ff]sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/32/jre1.6.0_23/bin/java" 1[/COLOR][/COLOR][/SIZE]
 
[COLOR=#000000][SIZE=3]Press Enter.[/SIZE][/COLOR]
 
[COLOR=#000000][SIZE=3]***Note:*** are you updating from a previous Java version, which you have removed manually? Then you'll need to execute the above command twice, because you'll get an error message the first time.[/SIZE][/COLOR]
 
 
[COLOR=#000000][SIZE=3]10. Tell the system, that the new Java must be the default:[/SIZE][/COLOR]
 
[SIZE=3][COLOR=#000000]Type (copy/paste):[/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][COLOR=#0000ff]sudo update-alternatives --set java /opt/java/32/jre1.6.0_23/bin/java[/COLOR][/COLOR][/SIZE]
 
[COLOR=#000000][SIZE=3][COLOR=#000000][COLOR=#000000]Press Enter.[/COLOR][/COLOR][/SIZE]
 
 
[/COLOR]
**[SIZE=3][COLOR=#000000][B]Install the Firefox plugin**[/COLOR][/SIZE][/B]
 
[SIZE=3][COLOR=#000000]11. Installing the Firefox plugin is simple. First execute the following command, in order to create a certain folder (if it doesn't exist already).[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#000000]Type in the terminal (copy/paste):[/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][COLOR=#0000ff]mkdir ~/.mozilla/plugins[/COLOR][/COLOR][/SIZE]
 
[COLOR=#000000][SIZE=3]Press Enter.[/SIZE][/COLOR]
 
[COLOR=#000000][SIZE=3]If it exists already, you'll see a notification of that.[/SIZE][/COLOR]
 
 
[COLOR=#000000][SIZE=3]12. Now remove the IcedTea plugin, if it has been installed.[/SIZE][/COLOR]
 
[SIZE=3][COLOR=#000000]Type (copy/paste):[/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][COLOR=#0000ff]sudo apt-get remove icedtea6-plugin[/COLOR][/COLOR][/SIZE]
 
[COLOR=#000000][SIZE=3]Press Enter.[/SIZE][/COLOR]
 
 
[COLOR=#000000][SIZE=3]13. Remove a former version of the Java plugin (may or may not be present, run the command just to make sure).[/SIZE][/COLOR]
 
[SIZE=3][COLOR=#000000]Type (copy/paste):[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#000000][COLOR=#0000ff]rm ~/.mozilla/plugins/libnpjp2.so[/COLOR][/COLOR][/SIZE]
 
[COLOR=#000000][SIZE=3]Press Enter.[/SIZE][/COLOR]
 
 
[COLOR=#000000][SIZE=3]14. Now you can install the plugin, by creating a symbolic link (you tell Firefox, where the plugin is located).[/SIZE][/COLOR]
 
[SIZE=3][COLOR=#000000][COLOR=#0000ff][COLOR=#000000]Type (copy/paste):[/COLOR][/COLOR][/COLOR][/SIZE]
[COLOR=#000000][COLOR=#000000][SIZE=3][COLOR=#000000][COLOR=#0000ff]ln -s /opt/java/32/jre1.6.0_23/lib/i386/libnpjp2.so ~/.mozilla/plugins/[/COLOR][/COLOR][/SIZE]
 
[COLOR=#000000][SIZE=3]Press Enter.[/SIZE][/COLOR]
 
 
[/COLOR][/COLOR]
**[SIZE=3][COLOR=#000000][COLOR=#0000ff][B][COLOR=#000000]Final check[/COLOR]**[/COLOR][/COLOR][/SIZE][/B]
 
[SIZE=3][COLOR=#000000]Now close and restart Firefox. Check if everything has succeeded. Type in the url bar of Firefox ***(not in the terminal!)***:[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#000000][COLOR=#0000ff]about:plugins[/COLOR][/COLOR][/SIZE]
 
[COLOR=#000000][SIZE=3]Press Enter.[/SIZE][/COLOR]
 
[COLOR=#000000][SIZE=3]And scroll down, until you see something approximately similar to this:[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3][COLOR=#0000ff]Java(TM) Plug-in 1.6.0_23[/COLOR][/SIZE]
 
[SIZE=3]You can also use this website:[/SIZE]
[SIZE=3][[COLOR=#0033cc]http://java.com/en/download/installed.jsp[/COLOR]]("http://java.com/en/download/installed.jsp")[/SIZE]
 
 
[/COLOR]
**[SIZE=3][COLOR=#000000][B]Other user accounts: repeat three commands**[/COLOR][/SIZE][/B]
 
[SIZE=3][COLOR=#000000]Are there any other user accounts on the computer? Then repeat the following three commands in each user account:[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#000000][COLOR=#0000ff]rm ~/.mozilla/plugins/libnpjp2.so[/COLOR][/COLOR][/SIZE]
 
[COLOR=#000000][SIZE=3]and then (in case the plugins folder doesn't exist yet):[/SIZE][/COLOR]
 
[COLOR=#000000][SIZE=3][COLOR=#000000]mkdir ~/.mozilla/plugins[/COLOR][/SIZE][/COLOR]
 
[SIZE=3][COLOR=#000000]and then:[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#000000][COLOR=#0000ff][COLOR=#000000][COLOR=#0000ff]ln -s /opt/java/32/jre1.6.0_23/lib/i386/libnpjp2.so ~/.mozilla/plugins/[/COLOR][/COLOR][/COLOR][/COLOR][/SIZE][COLOR=#000000]
[/COLOR]
 
 
**[SIZE=3][COLOR=#000000][B]Sun Java 6 Plugin Control Panel**[/COLOR][/SIZE][/B]
 
[SIZE=3][COLOR=#000000]You can call up the Control Panel as follows (in each user account):[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#000000]Type (copy/paste):[/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][COLOR=#0000ff]/opt/java/32/jre1.6.0_23/bin/ControlPanel[/COLOR][/COLOR][/SIZE]
 
[COLOR=#000000][SIZE=3]Press Enter.[/SIZE][/COLOR]
 
[COLOR=#000000][SIZE=3]***Note:*** this command is only for JRE update 23. You'll need to adapt it when you use another version.[/SIZE][/COLOR]
 
 
 
**[SIZE=3][COLOR=#000000][B]Removal**[/COLOR][/SIZE][/B]
 
[SIZE=3][COLOR=#000000]Do you wish to remove JRE again? It's very easy, to remove a manually installed JRE. As follows:[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#000000]Close Firefox (otherwise the java plugin will be in use).[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#000000]Now open file manager Nautilus with root rights, using the following terminal command.[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#000000]Applications - Accessories - Terminal[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#000000]Type (copy/paste):[/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][COLOR=#0000ff]gksudo nautilus[/COLOR][/COLOR][/SIZE]
 
[COLOR=#000000][SIZE=3]Press Enter.[/SIZE][/COLOR]
 
[COLOR=#000000][SIZE=3]File system - opt[/SIZE][/COLOR]
 
[COLOR=#000000][SIZE=3]Click on the folder [COLOR=#0000ff]java[/COLOR] and delete it.[/SIZE][/COLOR]
 
[SIZE=3][COLOR=#000000]Then remove the Java plugin:[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#000000]Type in the terminal (copy/paste):[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#000000][COLOR=#0000ff]rm ~/.mozilla/plugins/libnpjp2.so[/COLOR][/COLOR][/SIZE]
 
[SIZE=3]Press Enter.[/SIZE]

---

### Post by Legeril on 2010-12-31
Bludgard that installation worked perfectly, no problems at all.

I'm updated and feel clean again, thanks so much for your time and help

---

### Post by bludgard on 2010-12-31
Glad I could contribute.
 
Happy gaming,Legeril.\\:D/
 
One

---

### Post by ~Maxx on 2010-12-31
bludgard - you're a godsend!  I've been fighting this thing for two days so my wife can play her Pogo.com games and quit driving me nuts!  Worked like a charm!

Wife = :p

~Maxx = :guitar:

All the best to ya!

---

### Post by bludgard on 2010-12-31
Yeah.My wife loves her POGO,too!She prefers Windows/IE8 for that is what she is used to and there aren't the flash or Java issues.
 
However,my OCD wouldn't let me rest until I had it nailed in Ubuntu/Firefox as well.
 
Took me a few days and a lot of frustration to find the answer.
 
Thanks to oldos2er,another forum member,for providing such a useful post.=D>
 
Someone should really contact Java and let them know that their "Instructions" for install are a little too cryptic for the average user like me to understand.
 
That being said,you are welcome.
 
One

---

### Post by bludgard on 2011-01-01
What happened to the other links provided by another poster?
 
Something about .deb files?
 
Just curious.Or am I in the wrong thread?
 
One

---

