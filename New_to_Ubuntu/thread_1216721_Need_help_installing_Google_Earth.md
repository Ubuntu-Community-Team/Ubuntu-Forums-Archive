---
title: "Need help installing Google Earth"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by AlanInVancouverBC on 2009-07-18
I've tried to search this, here and on other sites, for hours/weeks. 
(1) I have a Google Earth installed, (and 3 compressed pkgs) that doesn't work and neither Synaptic nor Applications/Add-Remove can see it. But it's there! In my Opt folder. 3 copies in my var/cache/apt/archives. In user/local/share/applications. In user/share/aplnk. I'd like to delete all files associated with Google Earth, and then reinstall (hopefully) properly. 
:evil::evil:But first....
(2) This is my computer, and mine alone! Yet I don't have root priveleges, nor admin priveleges, nor owner. So I can't delete, nor access certain folders (such as: I can't create a /root/googleearth directory or /root/googleearth/cache directory. So it goes to the home/alan(my name)/filename.

Frustrated in Vancouver BC

---

### Post by aysiu on 2009-07-18
This will help you out:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

To install Google Earth, you need to add the Medibuntu repositories. More details here:
[http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources)
[https://help.ubuntu.com/community/GoogleEarth#Installation](https://help.ubuntu.com/community/GoogleEarth#Installation)

---

### Post by Rocket2DMn on 2009-07-18
You can still set yourself up with sudo/root privileges on the machine.  You will need to reboot into the Recovery Mode kernel at the Grub prompt.

Rather than add your user to the sudoers file, we'll just add you to the "admin" group which has full sudo access.  The default user on an Ubuntu machine is automatically part of this group which is why they have sudo privileges out of the box.  If you choose the root shell when booting into the recovery mode kernel, you will have a root prompt.  Run
```
usermod -G admin *yourusername*
```
Substitute your username for *yourusername*.  Then run
```
su *yourusername*
groups
```
You should see "admin" listed as one of the groups.  Now exit the su and reboot
```
exit
reboot
```
Login normally and you should have access to the sudo command.  With this you can install/uninstall programs among other things.

---

### Post by aysiu on 2009-07-18
> **Rocket2DMn said:**
> You can still set yourself up with sudo/root privileges on the machine.  You will need to reboot into the Recovery Mode kernel at the Grub prompt.

Rather than add your user to the sudoers file, we'll just add you to the "admin" group which has full sudo access.  The default user on an Ubuntu machine is automatically part of this group which is why they have sudo privileges out of the box.  If you choose the root shell when booting into the recovery mode kernel, you will have a root prompt.  Run
```
usermod -G admin *yourusername*
```
Substitute your username for *yourusername*.  Then run
```
su *yourusername*
groups
```
You should see "admin" listed as one of the groups.  Now exit the su and reboot
```
exit
reboot
```
Login normally and you should have access to the sudo command.  With this you can install/uninstall programs among other things.
I may be wrong, but I don't think the problem is that the OP isn't a sudoer. We'll see.

---

### Post by Rocket2DMn on 2009-07-18
> **aysiu said:**
> I may be wrong, but I don't think the problem is that the OP isn't a sudoer. We'll see.

He said, "Yet I don't have root priveleges, nor admin priveleges, nor owner."
Perhaps the OP doesn't know how to use sudo?

Alan, if you don't know what we're talking about, I suggest reading up on root/sudo at [uhelp]community/RootSudo[/uhelp]

---

### Post by AlanInVancouverBC on 2009-07-18
Ok. Thanks for the immediate help so far. But...

I rebooted into recovery and followed the suggested terminal commands and exited and rebooted normally. Without effect.
I still have 3 downloads of GE and no way to get them to load to the root directories that my original post suggested.
This is a recent 9.04 OS load, without changes in the install. I thought I would have "out of the box" admin/owner priveleges. I think I did with 8.04. I have gone into System/Admin/Authorizations and gave myself total freedom to change any/everything. Yes, there are inherent problems doing that, but my frustration overcame my logic.
How can I delete these downloaded, compressed GE files and start over?
Again, something odd, Add/Remove says I don't have GE installed, but in Applications/Internet I HAVE a GE listed (which starts but fails in not being able to install to the right, root, directories).
p.s. When are the "Thanks" buttons returning?

---

### Post by Rocket2DMn on 2009-07-18
What happens if you run
```
sudo apt-get remove --purge googleearth-package
```

The file at /var/cache/apt/archives is normal - this is where Ubuntu downloads files when it gets them from the repositories.  Don't worry about this.  If you want to clean out downloaded installers, run
```
sudo apt-get clean
```

There shouldn't be any need to create /root/googleearth or /root/googleearth/cache - what directions are you following anyway?  Do you have a link that you can show us?

---

### Post by AlanInVancouverBC on 2009-07-18
Thanks for the quick reply.
Using: sudo apt-get remove --purge googleearth-package
It returned that there were no pkgs to remove.
Using: sudo apt-get clean
It returned a prompt. I don't know what else I would see there.
As to "what directions are you following anyway? Do you have a link that you can show us?", I'm just using Synaptic tfile:///home/alan/Desktop/Screenshot-Could%20Not%20Create%20Folder.png
o install GE and installing 3 packages: Google Earth and Google Earth Data and lib32nss-mdns (what the latter is I don't know). Synaptic then informs me the changes have been applied.
When I click on the shortcut in Applications/Internet/Google Earth, I get these screenshots:

---

### Post by Rocket2DMn on 2009-07-18
At first it is trying to create directories for the root user, but you're not running the application as root (which is good).  It is then creating the cache folders in your home directory, which is correct.

I thought that Google Earth was in the repositories, but I guess it's not - that package is just to help build Google Earth.  You need to download Google Earth from - [http://earth.google.com/](http://earth.google.com/)
This will get a you .bin file.  Download it to your home directory, then open a terminal and run
```
chmod +x GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```
The installer will run, and you should be able to accept the defaults.

---

### Post by aysiu on 2009-07-18
It is in the repositories. It's in the Medibuntu repositories:
[http://packages.medibuntu.org/jaunty/googleearth.html](http://packages.medibuntu.org/jaunty/googleearth.html)

**Step 1: Add Medibuntu**
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

**Step 2: Install Google Earth**
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Rocket2DMn on 2009-07-18
My bad, I thought I had Medibuntu enabled but I didn't see googleearth.  Thanks for clearing that up, aysiu.

Alan, if you already followed my directions, it is easy to uninstall Google Earth, simply navigate to /home/alan/google-earth and run the uninstall shell script (when prompted, select Run in Terminal).  That's it!  Then you can install googleearth from the repositories just like other software in Ubuntu.

---

### Post by AlanInVancouverBC on 2009-07-18
"Code:
chmod +x GoogleEarthLinux.bin
./GoogleEarthLinux.bin
The installer will run, and you should be able to accept the defaults."

So I have GE on my desktop as a *.bin file. I used "sh" to open it. I got a terminal window popup (I can't printscreen it for some reason). It says (edited for brevity):

....failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
loki_setup: Suspect size value for option option 

/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
loki_setup: Suspect size value for option option

Nevertheless, the GE setup window appears with a "begin install" button. And when I click on that, I get the 3 error windows noted in my previous message.

I'm using 64-bit architecture. But other than the coincidence of 64 showing up in the error report above, I wouldn't think that would matter. I can install 32-bit pgms on 64-bit architecture.
p.s. twice the double word: "option option" showed up in the terminal window.

Thanks to all again for your time and thoughts.

---

### Post by oldos2er on 2009-07-18
> **AlanInVancouverBC said:**
> "Code:
chmod +x GoogleEarthLinux.bin
./GoogleEarthLinux.bin
The installer will run, and you should be able to accept the defaults."

So I have GE on my desktop as a *.bin file. I used "sh" to open it. I got a terminal window popup (I can't printscreen it for some reason). It says (edited for brevity):

....failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
loki_setup: Suspect size value for option option 

/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
loki_setup: Suspect size value for option option


 Do you have ia32-libs installed? Which version of GE are you trying to install?

---

### Post by AlanInVancouverBC on 2009-07-18
Thanks for your reply.
Yes, I have ia32-libs installed. I'm downloading GE 5.

---

### Post by oldos2er on 2009-07-18
I'm not sure what else to suggest. Perhaps try getlibs if you haven't already: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by AlanInVancouverBC on 2009-07-19
In trying sudo apt-get to reinstall GE, this was part of the report. What am I missing here?


Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Setting up googleearth (5.0.11337.1968-0medibuntu10) ...

---

### Post by Rocket2DMn on 2009-07-19
Alan,
I got the same thing when I installed, it doesn't seem to affect the program.  You should be able to use Google Earth now.

---

### Post by AlanInVancouverBC on 2009-07-19
"I got the same thing when I installed, it doesn't seem to affect the program. You should be able to use Google Earth now."
I'm unsure to what you are commenting.

This morning I used Terminal to delete all folders and files related to GE. (What a good way to learn some bash commands!)
I was thinking that there might be some rogue file or corrupt file that is blocking creating folders, thus me getting the error messages noted in my Comment #8 above, yesterday. Well, when I reinstalled GE5 it didn't work. I'm still getting those error messages. BTW I tried installing GE4 without success.

Very puzzling......

With a previous install of Ubuntu 9.04 it worked. In fact I have been creating a geographical autobiography in GE. I want to get back at it. My GE history is saved (I hope) on a Google server somewhere (I hope).

Thanks again for everyone's help.

---

### Post by unutbu on 2009-07-19
Alan, would you please run 
```

sudo find / -name "*googleearth*" -print
```

This will print all files on your machine that have the word "googleearth" in it.
This command will take a while to complete.

Then post the output.
This may help us figure out what's going on, or if there is more stray stuff which should be deleted. Note that deleting files manually is not the proper way to delete software. Binary versions of googleearth come with an uninstall script (I think), and deb packages can be removed with synaptic of course.

It is also possible that GE4 and GE5 both create ~/.googleearth in your home account, and they conflict. So the solution may be as simple as deleting your ~/.googleearth account and letting GE5 create a new one.

---

### Post by AlanInVancouverBC on 2009-07-26
Thanks for your continued assistance on this. I know it's a puzzle.
Here's the output from your suggestion above.
Alan

alan@alan:~$ sudo find / -name "*googleearth*" -print
[sudo] password for alan: 
/root/.googleearth
/home/alan/.local/share/mime/packages/googleearth-mimetypes.xml
/home/alan/.local/share/Trash/info/googleearth-data_5.0.11337.1968-0medibuntu10_all.deb.trashinfo
/home/alan/.local/share/Trash/info/Google-googleearth.3.desktop.trashinfo
/home/alan/.local/share/Trash/info/googleearth-bin.2.trashinfo
/home/alan/.local/share/Trash/info/googleearth-icon.2.png.trashinfo
/home/alan/.local/share/Trash/info/googleearth.4.trashinfo
/home/alan/.local/share/Trash/info/googleearth-mimetypes.2.xml.trashinfo
/home/alan/.local/share/Trash/info/googleearth_5.0.11337.1968-0medibuntu10_amd64.deb.trashinfo
/home/alan/.local/share/Trash/info/libgoogleearth_lib.2.so.trashinfo
/home/alan/.local/share/Trash/info/googleearth.3.trashinfo
/home/alan/.local/share/Trash/info/Google-googleearth.6.desktop.trashinfo
/home/alan/.local/share/Trash/info/Google-googleearth.4.desktop.trashinfo
/home/alan/.local/share/Trash/info/googleearth-mimetypes.3.xml.trashinfo
/home/alan/.local/share/Trash/info/googleearth.2.xpm.trashinfo
/home/alan/.local/share/applications/Google-googleearth.desktop
/home/alan/.googleearth
/home/alan/.kde/share/applnk/Google-googleearth.desktop
/home/alan/.gnome/apps/Google-googleearth.desktop
/var/cache/apt/archives/googleearth-data_5.0.11337.1968-0medibuntu10_all.deb
/var/cache/apt/archives/googleearth_5.0.11337.1968-0medibuntu10_amd64.deb
alan@alan:~$

---

### Post by AlanInVancouverBC on 2009-07-30
I deleted all references to googleearth by copying the command below, but instead of -print I put -delete.
Now that did all but /root/.googleearth.
Then I re-downloaded GoogleEarth (2 files) and installed, with the same outcome as noted above, with the 3 screenshots as shown above. Still can't get it .....................................................................................................................................................................:confused:
then I did a search as noted above for all "googleearth" files and got this:
alan@alan:~$ sudo find / -name "*googleearth*" -print
/root/.googleearth
/home/alan/.googleearth
/var/lib/dpkg/info/googleearth-data.list
/var/lib/dpkg/info/googleearth-data.postinst
/var/lib/dpkg/info/googleearth.postinst
/var/lib/dpkg/info/googleearth.postrm
/var/lib/dpkg/info/googleearth.md5sums
/var/lib/dpkg/info/googleearth-data.md5sums
/var/lib/dpkg/info/googleearth.templates
/var/lib/dpkg/info/googleearth-data.preinst
/var/lib/dpkg/info/googleearth.list
/var/lib/dpkg/info/googleearth.config
/var/lib/dpkg/info/googleearth.preinst
/var/cache/apt/archives/googleearth-data_5.0.11337.1968-0medibuntu10_all.deb
/var/cache/apt/archives/googleearth_5.0.11337.1968-0medibuntu10_amd64.deb
/usr/share/mime/packages/googleearth.xml
/usr/share/doc/googleearth-data
/usr/share/doc/googleearth
/usr/share/googleearth
/usr/share/googleearth/googleearth.xpm
/usr/share/pixmaps/googleearth.xpm
/usr/share/applications/googleearth.desktop
/usr/share/man/man1/googleearth.1.gz
/usr/lib/mime/packages/googleearth
/usr/lib32/googleearth
/usr/lib32/googleearth/libgoogleearth_lib.so
/usr/lib32/googleearth/googleearth-bin
/usr/bin/googleearth
alan@alan:~$

---

### Post by unutbu on 2009-07-30
Alan, would you type
```

which googleearth
googleearth
```

in the terminal and post the output?

---

### Post by AlanInVancouverBC on 2009-07-31
alan@alan:~$ which googleearth
/usr/bin/googleearth
alan@alan:~$ googleearth
Warning: Unable to create prefs directory '/home/alan/.googleearth'. File exists.
alan@alan:~$

---

### Post by unutbu on 2009-07-31
I don't know, Alan. I am pretty much stumped. According to 

[https://answers.launchpad.net/ubuntu/+source/googleearth-package/+question/65654](https://answers.launchpad.net/ubuntu/+source/googleearth-package/+question/65654)

the solution to the error "Warning: Unable to create prefs directory..." is to remove the ~/.googleearth directory, but it seems like you've already tried that. :confused:

---

### Post by AlanInVancouverBC on 2009-08-02
I finally got it just now. 
Using the link you noted immediately above, relating to a user (Italian?) who was having similar difficulties
**[https://answers.launchpad.net/ubuntu/+source/googleearth-package/+question/65654](https://answers.launchpad.net/ubuntu/+source/googleearth-package/+question/65654)**
I used these commands:
wget [http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin)
chmod 700 GoogleEarthLinux.bin
sudo ./GoogleEarthLinux.bin

It worked!
Thankyou Unutbu! And all others who assisted in this problem-solving.

---

### Post by unutbu on 2009-08-02
I'm so glad you found a solution. Congrats :)

---

### Post by AlanInVancouverBC on 2009-08-02
No it didn't...
I'm getting other messages, like:
**libQtWebKit.so.4: cannot open shared object file: No such file or directory**
and:
**libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory**
and:
**setup.data/bin/Linux/amd64/setup.gtk2: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory**
and:
**loki_setup: Suspect size value for option option**

---

### Post by unutbu on 2009-08-02
Hm. Type
```

cat $(which googleearth)
```

You should see something like

```
#!/bin/bash
export LD_LIBRARY_PATH=/usr/lib/googleearth:"${LD_LIBRARY_PATH}"
cd /usr/lib/googleearth
exec /usr/lib/googleearth/googleearth-bin "$@"
```

The last line shows the path to the googleearth binary program
In the example above:
```

/usr/lib/googleearth/googleearth-bin
```

Using the path you see, then type
```

ldd /usr/lib/googleearth/googleearth-bin
```

This will list where googleearth is looking for shared libraries like libQtWebKit.so.4 and libgtk-x11-2.0.so.0
Please post the output. 

PS. These libraries are provided by libgtk2.0-0 and libqt4-webkit. See [http://packages.ubuntu.com/search?suite=jaunty&arch=any&mode=exactfilename&searchon=contents&keywords=libQtWebKit.so.4](http://packages.ubuntu.com/search?suite=jaunty&arch=any&mode=exactfilename&searchon=contents&keywords=libQtWebKit.so.4) and [http://packages.ubuntu.com/search?suite=jaunty&arch=any&mode=exactfilename&searchon=contents&keywords=libgtk-x11-2.0.so.0](http://packages.ubuntu.com/search?suite=jaunty&arch=any&mode=exactfilename&searchon=contents&keywords=libgtk-x11-2.0.so.0). Maybe all you need to do is install these packages, but the above output will help us make sure that googleearth is looking in the right place (especially if you have these packages already installed.)

---

### Post by HotShotDJ on 2009-08-02
Is there some reason why you are insisting on manually downloading files from Google?  Aysiu has given you instruction on how to enable the proper repository so that it can be very easily be installed using Ubuntu's native installation process.  Had you follwed Aysiu's instructions, you would have had Googleearth installed and running days ago.

---

### Post by AlanInVancouverBC on 2009-08-02
Applying command: cat $(which googleearth) 
returns this:
[B]#!/bin/sh
#
# Google Earth startup script
#

# Function to find the real directory a program resides in.
# Feb. 17, 2000 - Sam Lantinga, Loki Entertainment Software
FindPath()
{
    fullpath="`echo $1 | grep /`"
    if [ "$fullpath" = "" ]; then
        oIFS="$IFS"
        IFS=:
        for path in $PATH
        do if [ -x "$path/$1" ]; then
               if [ "$path" = "" ]; then
                   path="."
               fi
               fullpath="$path/$1"
               break
           fi
        done
        IFS="$oIFS"
    fi
    if [ "$fullpath" = "" ]; then
        fullpath="$1"
    fi

    # Is the sed/ls magic portable?
    if [ -L "$fullpath" ]; then
        #fullpath="`ls -l "$fullpath" | awk '{print $11}'`"
        fullpath=`ls -l "$fullpath" |sed -e 's/.* -> //' |sed -e 's/\*//'`
    fi
    dirname $fullpath
}

# Set the home if not already set.
if [ "${GOOGLEEARTH_DATA_PATH}" = "" ]; then
    GOOGLEEARTH_DATA_PATH="`FindPath $0`"
fi

LD_LIBRARY_PATH=.:${GOOGLEEARTH_DATA_PATH}:${LD_LIBRARY_PATH}
export LD_LIBRARY_PATH

# Let's boogie!
if [ -x "${GOOGLEEARTH_DATA_PATH}/googleearth-bin" ]
then
	cd "${GOOGLEEARTH_DATA_PATH}/"
	exec "./googleearth-bin" "$@"
fi
echo "Couldn't run Google Earth (googleearth-bin). Is GOOGLEEARTH_DATA_PATH set?"
exit 1

# end of googleearth ...[/B]

Applying code: /usr/lib/googleearth/googleearth-bin
returns this:
**bash: /usr/lib/googleearth/googleearth-bin: No such file or directory**
Applying code: ldd /usr/lib/googleearth/googleearth-bin
returns this:
**ldd: /usr/lib/googleearth/googleearth-bin: No such file or directory**

---

### Post by AlanInVancouverBC on 2009-08-02
I have tried Synaptic to get GE after installing Medibuntu. I have tried Add/Remove in Applications. I have tried Terminal.
To the best of my limited ability, I have tried every method offered. This morning I came close. 
My knowledge is limited with Linux/Ubuntu. I have 23 years with DOS/Windows and ~1 year with Ubuntu.
I think there are issues with 64-bit motherborads, AMD64 cpus, the desire of GE to support the above, and maybe me.
I defer to all the helpers above, because I don't have the knowledge needed. 
I really want GE installed properly because I have spent considerable time on 8.10 creating a geographical autobiography (extensive since I'm 62 years old). It's stored (I hope) on a GE server somewhere.

Alan
Frustrated in Vancouver BC Canada

---

### Post by AlanInVancouverBC on 2009-08-02
The reply immediately above is in response to HotShotDJ.
Aln

---

### Post by unutbu on 2009-08-02
Alan, thanks for your patience. Would you please post
```

sudo find / -name "*googleearth*" -print
```

again?

---

### Post by Clorow on 2009-08-02
Google Earth is the messiest, most confusing package I've seen. Try this:

```
sudo apt-get install googleearth-package && sudo make-googleearth-package
```

Then wait for it to work its magic, and after it's done, install the cute little *.deb that showed up in your home directory.

---

### Post by HotShotDJ on 2009-08-02
> **AlanInVancouverBC said:**
> I think there are issues with 64-bit motherborads, AMD64 cpus, the desire of GE to support the above, and maybe me.Ok... I understand better your frustration.  I have no experience with 64 bit hardware or software (something that will be changing soon, I hope!).  I'm wondering if you might want to post in the [x86 64-bit User]("http://ubuntuforums.org/forumdisplay.php?f=34")s forum.  The people who monitor that forum are very familiar with the issues surrounding 32 bit compatibility under 64 bit Ubuntu.  They may be able to help you get things sorted.  There's no need to repost everything from this thread... just link to it for them to reference.

I understand your frustration.  My computer experience is quite the opposite of yours.  I learned under Unix in the late 70's and into the 80's, then worked with various DOS systems (CP/M, IBM, MS), and then OS/2 Warp 3 became my primary OS for several years in the 90's.  I only used Windows (Win98, WinME, Win2000) for a few years before switching to Linux around 2001 -- just as WinXP was coming out.  Now, when I am forced to use Windows XP or (heaven forbid!) Vista, I am often quite lost when things go wrong.  Fortunately, the ITS department where I work is very responsive and help me out.

EDIT:  I didn't even think of googleearth-package as referenced by Clorow.  Try that first.  If you still have no joy, then try the forum I mentioned above.

---

### Post by AlanInVancouverBC on 2009-08-02
> **unutbu said:**
> Alan, thanks for your patience. Would you please post
```

sudo find / -name "*googleearth*" -print
```

again?
alan@alan:~$ **sudo find / -name "*googleearth*" -print**
[sudo] password for alan: 
/opt/google-earth/Google-googleearth.desktop
/opt/google-earth/googleearth-mimetypes.xml
/opt/google-earth/googleearth
/opt/google-earth/googleearth.xpm
/opt/google-earth/libgoogleearth_lib.so
/opt/google-earth/googleearth-bin
/opt/google-earth/googleearth-icon.png
/root/.googleearth
/home/alan/Desktop/Google-googleearth.desktop
/var/lib/dpkg/info/googleearth-data.list
/var/lib/dpkg/info/googleearth-data.postinst
/var/lib/dpkg/info/googleearth.postinst
/var/lib/dpkg/info/googleearth.postrm
/var/lib/dpkg/info/googleearth.md5sums
/var/lib/dpkg/info/googleearth-data.md5sums
/var/lib/dpkg/info/googleearth.templates
/var/lib/dpkg/info/googleearth-data.preinst
/var/lib/dpkg/info/googleearth.list
/var/lib/dpkg/info/googleearth.config
/var/lib/dpkg/info/googleearth.preinst
/var/cache/apt/archives/googleearth-data_5.0.11337.1968-0medibuntu10_all.deb
/var/cache/apt/archives/googleearth_5.0.11337.1968-0medibuntu10_amd64.deb
/usr/share/mime/packages/googleearth.xml
/usr/share/doc/googleearth-data
/usr/share/doc/googleearth
/usr/share/googleearth
/usr/share/googleearth/googleearth.xpm
/usr/share/pixmaps/googleearth.xpm
/usr/share/applications/googleearth.desktop
/usr/share/applnk/Google-googleearth.desktop
/usr/share/man/man1/googleearth.1.gz
/usr/local/share/mime/packages/googleearth-mimetypes.xml
/usr/local/share/applications/Google-googleearth.desktop
/usr/local/bin/googleearth
/usr/lib/mime/packages/googleearth
/usr/lib32/googleearth
/usr/lib32/googleearth/libgoogleearth_lib.so
/usr/lib32/googleearth/googleearth-bin
/usr/bin/googleearth
alan@alan:~$

---

### Post by unutbu on 2009-08-02
Alan, I think Clorow has a good idea. 

So let's try to remove the medibuntu GE package, and the GE installed from the .bin file, 
and then install Clorow's way.

To remove the medibuntu GE package:
```

sudo apt-get purge googleearth*
sudo apt-get autoremove

```

To remove GoogleEarthLinux.bin (from [http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin)) type

```
cd /opt/google-earth/
export DISPLAY=:0
sudo ./uninstall
```

Then try installing googleearth via the googleearth-package package:
```

sudo apt-get install googleearth-package && sudo make-googleearth-package --force
sudo dpkg -i googleearth_5.0.11733.9347+0.5.4-1_i386.deb
/usr/bin/googleearth

```

I purged GE v.4.2 from my machine and used the above commands to install GE v.5.0.11733.9347.

---

### Post by AlanInVancouverBC on 2009-08-03
Then try installing googleearth via the googleearth-package package:
Code:
[B]sudo apt-get install googleearth-package && sudo make-googleearth-package --force
[/B]
From the above command, I got a lot of terminal lines
(example: 
[B]Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libIGGui.so needed by ../usr/lib/googleearth/libcollada.so (its RPATH is '/usr/local/google/build/.pulse/data/recipes/34609195/base/googleclient/earth/client/scons-out/prod/lib:/usr/local/google/build/.pulse/data/recipes/34609195/base/googleclient/third_party/alchemy/files/newgap/install/LinuxOglRelease.A/lib:/usr/local/google/build/.pulse/data/recipes/34609195/base/googleclient/earth/client/thirdparty/lib-linux').)[/B]

ending up with this:
[B]dpkg-deb: building package `googleearth' in `./googleearth_5.0.11733.9347+0.5.4.1-1_amd64.deb'.
Success![/B]


Then I copied/pasted the next command:
** sudo dpkg -i googleearth_5.0.11733.9347+0.5.4-1_i386.deb**

and terminal returned this:
[B]dpkg: error processing googleearth_5.0.11733.9347+0.5.4-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 googleearth_5.0.11733.9347+0.5.4-1_i386.deb
alan@alan:/opt/google-earth$ [/B]

---

### Post by unutbu on 2009-08-03
I got reams of the same kind of warnings as the one you posted. Nevertheless, the program seems to work on my end, except for the fonts looking un-antialiased.

Since my machine is running the 32-bit os and you are running 64-bit,
our resultant debs have different names. Try: 
```

sudo dpkg -i googleearth_5.0.11733.9347+0.5.4.1-1_amd64.deb
```
(PS. You can also double-click on debs in nautilus to get them to install.)

---

### Post by AlanInVancouverBC on 2009-08-03
**[B][B]alan@alan:/opt/google-earth$ sudo dpkg -i **[/B]googleearth_5.0.11733.9347+0.5.4-1_i386.deb[/B]
dpkg: error processing googleearth_5.0.11733.9347+0.5.4-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 googleearth_5.0.11733.9347+0.5.4-1_i386.deb
**alan@alan:/opt/google-earth$ /usr/bin/googleearth**
/usr/lib/googleearth/googleearth-bin: symbol lookup error: /usr/lib/googleearth/libssl.so.0.9.8: undefined symbol: EVP_idea_cbc
**alan@alan:/opt/google-earth$ sudo dpkg -i **googleearth_5.0.11733.9347+0.5.4.1-1_amd64.deb
(Reading database ... 157456 files and directories currently installed.)
Preparing to replace googleearth 5.0.11733.9347+0.5.4.1-1 (using googleearth_5.0.11733.9347+0.5.4.1-1_amd64.deb) ...
Unpacking replacement googleearth ...
Setting up googleearth (5.0.11733.9347+0.5.4.1-1) ...

Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

**alan@alan:/opt/google-earth$ **

I'm sorry. I've come back full circle to the original screens noted way above (2 weeks ago), and now all I get is a google earth splash screen which disappears in about 5 seconds. That's it.

---

### Post by unutbu on 2009-08-03
Alan, please post the output of 

```
cd /opt/google-earth
ls -l                                          # List files in /opt/google-earth
dpkg --get-selections | grep google            # See what google packages are installed
sudo find / -name "googleearth*.deb" -print    # Find out where googleearth_5.0.11733.9347+0.5.4-1_amb64.deb is

```

---

### Post by AlanInVancouverBC on 2009-08-03
alan@alan:~$ cd /opt/google-earth
alan@alan:/opt/google-earth$ ls -l 
total 67664
-rw-r--r-- 1 root root 25982318 2009-08-03 08:24 googleearth_5.0.11733.9347+0.5.4.1-1_amd64.deb
-rw-r--r-- 1 root root 25606194 2009-05-05 20:00 GoogleEarthLinux.bin
lrwxrwxrwx 1 root root       21 2009-08-02 11:15 libcrypto.so.0.9.8.old -> /usr/lib/libcrypto.so
-rwxr-xr-x 1 root root  2244156 2009-08-02 11:21 libQtCore.so.4-bak
-rwxr-xr-x 1 root root  7305864 2009-08-02 11:21 libQtGui.so.4-bak
-rwxr-xr-x 1 root root   774340 2009-08-02 11:21 libQtNetwork.so.4-bak
-rwxr-xr-x 1 root root  7265852 2009-08-02 11:21 libQtWebKit.so.4-bak
alan@alan:/opt/google-earth$ dpkg --get-selections | grep google 
googleearth					install
googleearth-package				install
libgdata-google1.2-1				install
alan@alan:/opt/google-earth$ sudo find / -name "googleearth*.deb" -print
[sudo] password for alan: 
/opt/google-earth/googleearth_5.0.11733.9347+0.5.4.1-1_amd64.deb
/home/alan/googleearth_5.0.11733.9347+0.5.4.1-1_amd64.deb
/var/cache/apt/archives/googleearth-package_0.5.4.1~0ubuntu1_all.deb
alan@alan:/opt/google-earth$ 

thanks for not losing your patience.....

---

### Post by unutbu on 2009-08-03
Alan, if you could backup your personal data and then reinstall Jaunty, then install google earth, I wonder if that might be the easiest way to get it to work. 

The problems you are experiencing seem a bit peculiar to me -- certainly others running 64-bit Ubuntu must have successfully installed GE. I don't know what is different about your situation. 

You might want to try installing 32-bit version of Jaunty. That might be another way to avoid this issue you're having.

However, if reinstalling is not an option, then we can continue searching for the source of the problem, but know that this might take a lot of back and forth posting and it could be slow going since I would be fishing for a solution and not operating from real knowledge.

Please consider what path you think is best, then let us know.

---

### Post by AlanInVancouverBC on 2009-08-04
**I'm going to try to delete all references to GE.** Maybe with these 4 gone and my permissions all enabled, I might have a chance. (Still thinking of reinstalling 9.04 as a 32-bit OS.)

[B]I have 4 listed:
/root/.googleearth
/home/alan/.googleearth
/usr/share/doc/googleearth
/usr/lib/googleearth

I need help with this[/B]. I have printed out a list of bash commands, but I'm so new to this system (It's not DOS!) that I can't change directories or remove files--especially those that start with a dot, like /.googleearth. 

Further, when I go into Nautilus, I can't delete files. I get the message that I don't have permission to view the "Root" directory or delete files in my own directory/folder, even though this is my computer; I'm the only one logging in. I don't even use a logon and password; it just boots up.

---

### Post by unutbu on 2009-08-04
Alan, to understand how to run commands with root privileges, read this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

To remove a directory which requires root permissions (like /root/.googleearth), type
```

sudo rm -rf /root/.googleearth
```

Be very careful using this command. A misplaced space (between / and the rest of the path) can wipe out your entire Ubuntu installation.

Another method which you might like better is to run
```

gksu nautilus
```

This will launch a nautilus file browser with root privileges. You can then navigate to
/root/.googleearth and delete the directory using the file browser.
Note that nautilus hides files and directories that begin with a period by default.
To make so-called "hidden files" visible, press Ctrl-h. It toggles between hiding and unhiding the hidden files.

Also, if at all possible, try to delete software in some way other than manually removing files. If the directory, like /usr/lib/googleearth was installed by a deb package, then you should remove it via a package manager. Either type the command```


sudo dpkg -r googleearth
```
or click System>Admin>Synaptic. Search for the googleearth package and remove it using the Synaptic GUI.

If you remove bits and pieces of the googleearth package manually, then later on your package manager may complain about broken packages. Fixing this is possible, but tedious. It is much better not to get into that kind of mess in the first place.

To find out which package installed a file, run this command
```

dpkg -S /path/to/file
```

(replacing /path/to/file with the actual path to the file.)
For instance,
```

dpkg -S /usr/share/doc/googleearth
```

returns 
```

googleearth: /usr/share/doc/googleearth
```

This means that the googleearth package installed the /usr/share/doc/googleearth directory. Therefore, the correct way to remove the directory is to type
```

sudo dpkg -r googleearth
```
(or use Synaptic.)

Removing a package does not remove configuration directories in your home account however. 
So it is correct to use
```

sudo rm -rf /root/.googleearth
sudo rm -rf ~/.googleearth

```
to remove those directories.

In summary, I believe the commands you should issue are 
```

sudo dpkg -r googleearth
sudo rm -rf /root/.googleearth
rm -rf ~/.googleearth

```

---

### Post by AlanInVancouverBC on 2009-08-04
Wow. What a complete tutorial!
I've got 2 manuals, The Linux Starter Pack, by Paul Hudson, and The Ubuntu Pocket Guide and Reference, by Keir Thomas. Plus I found a website that alphabetizes bash commands (but they're just the core commands, without the triggers. I'm using all sources and all ideas. In parallel time with your reply, I reverted to the command list command from about 2 weeks ago (from you: sudo find / -name "*googleearth*" -print), augmented with the Termainal Help command to get triggers. I was unable to get the last reference to googleearth, in the root directory until your reply.
Now they are all gone.

---

### Post by AlanInVancouverBC on 2009-08-06
God! I feel like such an ***!
In searthing around the net for other suggestions prior to reinstalling 9.04 as a 32-bit OS, I came across an idea to delete the file: libcrypto.so.0.9.8 in the googleearth pkg, and let Ubuntu use its own (or words to that effect).
So I deleted that file. Still can't get GE to load. Same 3 error messages.
**And now I can't boot Ubuntu because that file is missing.**
How do I repair this?
I'm using the disk (64-bit) to load the temporary OS to get to the internet and post this.
Now that I've got this far in destroying my system, I'll backup my email stuff and download a 32-bit OS and start over......

---

### Post by unutbu on 2009-08-06
I think I know how to fix this.

Boot from the Jaunty LiveCD.
Open a terminal (Applications>Accessories>Terminal) and type
```

sudo fdisk -l
ls -l /usr/lib/libcrypto.so.0.9.8
```

(Note in both commands "-l" is a lowercase "L").
Then post the output.

---

### Post by AlanInVancouverBC on 2009-08-07
Here's the screenshot.

---

### Post by unutbu on 2009-08-07
Boot the LiveCD. Open a terminal and type

```

sudo mount /dev/sda1 /mnt                               		 # Mount the Ubuntu partition at /mnt
sudo cp /lib/libcrypto.so.0.9.8 /mnt/lib/libcrypto.so.0.9.8   		 # Copy the LiveCD's libcrypto to the corresponding location in the Ubuntu installation.
sudo ln -sf /mnt/lib/libcrypto.so.0.9.8 /mnt/usr/lib/libcrypto.so.0.9.8  # Create the analogous symlink
```

That's it. Then try booting into Ubuntu.

---

### Post by AlanInVancouverBC on 2009-08-08
worked like a charm.
Double thanks.
Where are the "Thanks" icons?
Now I will backup necessary files.
Then I will d/l and install a 32-bit OS.

---

### Post by unutbu on 2009-08-08
I'm glad it worked!
Thanks for the thanks. The button was martyred in name of server stability.
Good luck with the backup and reinstall.

---

### Post by AlanInVancouverBC on 2009-08-09
The re-install was easy, of course.
I only backed up my email. Easy recapture.
GE is now up and running. But I my saved places (remember? I had spent a lot of time creating a geographical autobiography. I thought it was saved somewhere on a GE server. NOT!) are gone. Need to re-create that and save it to somewhere (a floppy, flash, or hd) locally.

GE case closed. The fault lies with GE and 64-bit machines!

---

