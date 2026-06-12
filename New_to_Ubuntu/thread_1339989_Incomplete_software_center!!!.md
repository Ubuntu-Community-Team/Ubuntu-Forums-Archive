---
title: "Incomplete software center!!!"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by SwatKat on 2009-11-28
Hey all

Today when I opened software center, it was incomplete (Some departments were missing!). I have attached the screenshot. I ran software center from the terminal and got this

```
swat@ubuntu:~$ software-center
WARNING:root:'/usr/share/desktop-directories/Accessories.directory' has no name
WARNING:root:'/usr/share/desktop-directories/Accessibility.directory' has no name
WARNING:root:'/usr/share/desktop-directories/Games.directory' has no name
WARNING:root:'/usr/share/desktop-directories/Internet.directory' has no name
WARNING:root:'/usr/share/desktop-directories/Multimedia.directory' has no name
WARNING:root:'/usr/share/desktop-directories/Other.directory' has no name

```I checked in usr/share/desktop-directories and what do you know, those listed as having no name are not present at all!
I reinstalled software center from synaptic, but that didn't help. Any ideas as to why this might have happened ? How do I set it right?

---

### Post by 3rdalbum on 2009-11-28
None of those are present on my system either, but Software Center still works fine. Some of them have different names - for instance, it's "Game" not "Games".

What exactly is in /usr/share/desktop-directories?

---

### Post by wilee-nilee on 2009-11-28
Do you have the extra repositories ticked in software sources. I have seen comments about software center having some problems, but it may be in your case that the repos are not ticked. Personally I would always use synaptic or the terminal, but you would still need the repos for them to work.

---

### Post by SwatKat on 2009-11-28
> **wilee-nilee said:**
> Do you have the extra repositories ticked in software sources. I have seen comments about software center having some problems, but it may be in your case that the repos are not ticked. Personally I would always use synaptic or the terminal, but you would still need the repos for them to work.

That might be it! I had added some repos a few days ago, but was getting  error messages while updating the system. So I might have unchecked a required repository along with the faulty ones. But I don't know which. Could you please provide me with the list of default repos so I can check them back? Thanks!

---

### Post by wilee-nilee on 2009-11-28
Now I have everything ticked to work but some suggest that the unsupported and the pre-released are not good to have on unless you know what your doing but I have always had them ticked on since starting with Dapper and haven't seemed to have problems here are screen shots. [ATTACH]137871[/ATTACH]

[ATTACH]137872[/ATTACH]

---

### Post by SwatKat on 2009-11-28
> **3rdalbum said:**
> None of those are present on my system either, but Software Center still works fine. Some of them have different names - for instance, it's "Game" not "Games".

What exactly is in /usr/share/desktop-directories?

I  have a game.directory too. But I didn't see accessories, multimedia and other and jumped to conclusions

---

### Post by ibuclaw on 2009-11-28
Software Centre gets it's data from a file called "applications.menu"

Unless you've changed your Applications menu names, there should be no other reason why you may be getting this message.

Although, you can make sure that the correct packages are installed (unlikely to be the problem due to dependencies).
```
sudo apt-get install gnome-menus app-install-data
```

Regards
Iain

---

### Post by SwatKat on 2009-11-28
> **wilee-nilee said:**
> Now I have everything ticked to work but some suggest that the unsupported and the pre-released are not good to have on unless you know what your doing but I have always had them ticked on since starting with Dapper and haven't seemed to have problems here are screen shots. [ATTACH]137871[/ATTACH]

[ATTACH]137872[/ATTACH]
Thanks a lot for the screenshots. Could you please show me the default options in 'Other Software ' too. Thats where I added and unchecked the sources.

---

### Post by wilee-nilee on 2009-11-28
Sometimes people add to the source list and make mistakes can you post your source list run in terminal 
cat gedit /etc/apt/sources.list

---

### Post by SwatKat on 2009-11-28
> **tinivole said:**
> Software Centre gets it's data from a file called "applications.menu"

Unless you've changed your Applications menu names, there should be no other reason why you may be getting this message.

Although, you can make sure that the correct packages are installed (unlikely to be the problem due to dependencies).
```
sudo apt-get install gnome-menus app-install-data
```Could you also post the output of (if any):
```
find ~/.local -iname "applications.menu"
```Regards
Iain

Thanks. This is what I get
```
swat@ubuntu:~$ sudo apt-get install gnome-menus app-install-data
[sudo] password for swat: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-menus is already the newest version.
app-install-data is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
swat@ubuntu:~$ find ~/.local -iname "applications.menu"
swat@ubuntu:~$ 

```

---

### Post by SwatKat on 2009-11-28
> **wilee-nilee said:**
> Sometimes people add to the source list and make mistakes can you post your source list run in terminal 
cat gedit /etc/apt/sources.list

I get this :

swat@ubuntu:~$ cat gedit /etc/apt/sources.list
cat: gedit: No such file or directory
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
# deb [http://host/debian](http://host/debian) distribution section1 section2 section3
# deb-src [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable main
# deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable main contrib non-free
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe
swat@ubuntu:~$

---

### Post by wilee-nilee on 2009-11-28
> **SwatKat said:**
> Thanks a lot for the screenshots. Could you please show me the default options in 'Other Software ' too. Thats where I added and unchecked the sources.
I have a bunch of extras but here you go, I think the stock set up is just the Canonical 2 lines #3&4. If you had errors originaly were they because of no key being added.
[ATTACH]137881[/ATTACH]

Here is my source list but there are extras that you will see indicated in the screen shot as well.

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic main
# deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic main

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://ppa.launchpad.net/deluge-team/ppa/ubuntu](http://ppa.launchpad.net/deluge-team/ppa/ubuntu) karmic main
# deb-src [http://ppa.launchpad.net/deluge-team/ppa/ubuntu](http://ppa.launchpad.net/deluge-team/ppa/ubuntu) karmic main
deb [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) karmic main 
# deb-src [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) karmic main

---

### Post by ibuclaw on 2009-11-28
> **SwatKat said:**
> Thanks. This is what I get
```

swat@ubuntu:~$ find ~/.local -iname "applications.menu"
swat@ubuntu:~$ 

```

Ahh, that file is kept inside ~/.config, sorry.
```
find ~/.config -iname "applications.menu"
```
If anywhere - it should be in ~/.config/menus

Regards
Iain

---

### Post by wilee-nilee on 2009-11-28
> **tinivole said:**
> Ahh, that file is kept inside ~/.config, sorry.
```
find ~/.local -iname "applications.menu"
```
If anywhere - it should be in ~/.config/menus

Regards
Iain

Hey man do you see the bottom of his source list the extra terminal line.

So Swatcat that last line in the source list is a red flag for removal run in the terminal.
sudo gedit /etc/apt sources.list 
and remove the last line which looks exactly like the line from your terminal then click save and close it.

---

### Post by ibuclaw on 2009-11-28
> **SwatKat said:**
> Thanks. This is what I get
```

swat@ubuntu:~$ find ~/.local -iname "applications.menu"
swat@ubuntu:~$ 

```

Failing that:
```
gedit /usr/share/app-install/desktop/applications.menu
```
and post the contents.

---

### Post by SwatKat on 2009-11-28
> **wilee-nilee said:**
> Hey man do you see the bottom of his source list the extra terminal line.

So Swatcat that last line in the source list is a red flag for removal run in the terminal.
sudo gedit /etc/apt sources.list 
and remove the last line which looks exactly like the line from your terminal then click save and close it.

I get this ( Screenshot) when I run

sudo gedit /etc/apt sources.list

---

### Post by SwatKat on 2009-11-28
> **SwatKat said:**
> I get this ( Screenshot) when I run

sudo gedit /etc/apt sources.list
oops, I forgot to attach the screenshot!

---

### Post by SwatKat on 2009-11-28
> **tinivole said:**
> Failing that:
```
gedit /usr/share/app-install/desktop/applications.menu
```and post the contents.


Here you go

<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
 "http://www.freedesktop.org/standards/menu-spec/1.0/menu.dtd">

<Menu>

  <Name>Applications</Name>
  <Directory>Applications.directory</Directory>

  <AppDir>.</AppDir>

  <!-- we disable those here, otherwise we see e.g. wine menus -->
  <!-- Read standard .directory and .desktop file locations -->
  <!-- <DefaultAppDirs/> -->
  <!-- Read in overrides and child menus from applications-merged/ -->
  <!-- <DefaultMergeDirs/> -->

  <DefaultDirectoryDirs/>

  <!-- Accessories submenu -->
  <Menu>
    <Name>Accessories</Name>
    <Directory>Accessories.directory</Directory>
    <Include>
      <And>
        <Category>Utility</Category>
        <Not>
          <Category>System</Category>
        </Not>
      </And>
    </Include>
  </Menu> <!-- End Accessories -->

  <!-- Accessibility submenu -->
  <Menu>
    <Name>Accessibility</Name>
    <Directory>Accessibility.directory</Directory>
    <Include>
      <And>
        <Category>Accessibility</Category>
        <Not>
          <Category>Settings</Category>
        </Not>
      </And>
    </Include>
  </Menu> <!-- End Accessibility -->

  <!-- Development Tools -->
  <Menu>
    <Name>Development</Name>
    <Directory>Development.directory</Directory>
    <Include>
      <And>
        <Category>Development</Category>
      </And>
      <Filename>emacs.desktop</Filename>
    </Include>
  </Menu> <!-- End Development Tools -->

  <!-- Education -->
  <Menu>
    <Name>Education</Name>
    <Directory>Education.directory</Directory>
    <Include>
      <And>
        <Category>Education</Category>
      </And>
    </Include>
  </Menu> <!-- End Education -->

  <!-- Games -->
  <Menu>
    <Name>Games</Name>
    <Directory>Games.directory</Directory>
    <Include>
      <And>
        <Category>Game</Category>
      </And>
    </Include>
  </Menu> <!-- End Games -->

  <!-- Graphics -->
  <Menu>
    <Name>Graphics</Name>
    <Directory>Graphics.directory</Directory>
    <Include>
      <And>
        <Category>Graphics</Category>
      </And>
    </Include>
  </Menu> <!-- End Graphics -->

  <!-- Internet -->
  <Menu>
    <Name>Internet</Name>
    <Directory>Internet.directory</Directory>
    <Include>
      <And>
        <Category>Network</Category>
      </And>
    </Include>
  </Menu>   <!-- End Internet -->

  <!-- Multimedia -->
  <Menu>
    <Name>Multimedia</Name>
    <Directory>Multimedia.directory</Directory>
    <Include>
      <And>
        <Category>AudioVideo</Category>
      </And>
    </Include>
  </Menu>   <!-- End Multimedia -->

  <!-- Office -->
  <Menu>
    <Name>Office</Name>
    <Directory>Office.directory</Directory>
    <Include>
      <And>
        <Category>Office</Category>
      </And>
    </Include>
  </Menu> <!-- End Office -->

  <!-- System Tools-->
  <Menu>
    <Name>System</Name>
    <Directory>System-Tools.directory</Directory>
    <Include>
      <And>
        <Category>System</Category>
<!--        <Not><Category>Settings</Category></Not> -->
      </And>
    </Include>
  </Menu>   <!-- End System Tools -->

  <!-- Other -->
  <Menu>
    <Name>Other</Name>
    <Directory>Other.directory</Directory>
    <OnlyUnallocated/>
    <Include>
      <And>
        <Category>Application</Category>
        <Not><Category>Core</Category></Not>
<!--        <Not><Category>Settings</Category></Not> -->
      </And>
    </Include>
  </Menu> <!-- End Other -->


</Menu> <!-- End Applications -->

---

### Post by wilee-nilee on 2009-11-28
> **SwatKat said:**
> I get this ( Screenshot) when I run

sudo gedit /etc/apt sources.list


sorry I left out a / and hit space instead my bad.
sudo gedit /etc/apt/sources.list

---

### Post by SwatKat on 2009-11-28
> **wilee-nilee said:**
> sorry I left out a / and hit space instead my bad.
sudo gedit /etc/apt/sources.list

I just want to make sure I'm doing this right. Here is my sources.list that I get when I run sudo gedit /etc/apt/sources.list

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
# deb [http://host/debian](http://host/debian) distribution section1 section2 section3
# deb-src [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable main
# deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable main contrib non-free
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe


What exactly do you want me to remove? The last time ( I reply to tinivole's post) I ran** cat** gedit /etc/apt/sources.list . So I had an extra terminal line.

---

### Post by ibuclaw on 2009-11-28
> **SwatKat said:**
> Here you go

<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
 "http://www.freedesktop.org/standards/menu-spec/1.0/menu.dtd">

<Menu>
*SNIP*
</Menu> <!-- End Applications -->

And that file is not correct to your system setup.

Run:
```
dpkg -l app-install-data
```
to get the version number of that package. It *should* be '**0.9.10.11**'
If not try any of the following steps:


**PLAN A**
Try and see if you can downgrade it to that version

If you can't find a way to downgrade easily:
**PLAN B**
```

sudo touch /etc/apt/preferences
sudo ln -s /etc/apt/preferences /var/lib/synaptic/preferences

```
Then
```
gksu gedit /etc/apt/preferences
```
And put this inside the file and save.
```

Package: app-install-data
Pin: version 0.9.10.11
Pin-Priority: 1001


```
Then run:
```
sudo apt-get install -f
```


If still not resolved:
**PLAN C**
```

sudo rm /etc/apt/preferences
sudo touch /etc/apt/preferences
sudo dpkg-divert --local --rename --add /usr/share/app-install/desktop/applications.menu

```
Then run:
```
gksu gedit /usr/share/app-install/desktop/applications.menu
```
And paste in the entire contents listed in this link:
[http://paste.ubuntu.com/330237](http://paste.ubuntu.com/330237)

Regards
Iain

---

### Post by wilee-nilee on 2009-11-28
I didn't realize that the cat output was showing the bottom of the terminal it looks okay, my mistake, I had seen another person with a incorrect line so I had not realized what I was looking at.

I think tinyvole and you will get things squared away.

---

### Post by SwatKat on 2009-11-28
Plan C worked tinivole , Thanks a bunch!!!
Here is a screenshot of my software center now. I know its not needed, but I'm just happy:P. Thanks to wilee-nilee too for showing interest.

---

### Post by wilee-nilee on 2009-11-28
> **SwatKat said:**
> Plan C worked tinivole, Thanks a bunch!!!
Here is a screenshot of my software center now. I know its not needed, but I'm just happy:P. Thanks to wilee-nilee to for showing interest.

I only got in the way but thanks. ;)

---

