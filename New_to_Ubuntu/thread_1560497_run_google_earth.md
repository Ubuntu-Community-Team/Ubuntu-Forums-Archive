---
title: "run google earth"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by ub9876 on 2010-08-24
i got the package and installed..  how to get google earth on desktop  and to run     from terminal..

---

### Post by dtoronto on 2010-08-24
Are you running gearth with WINE?

---

### Post by ub9876 on 2010-08-24
no   do i need it

---

### Post by gbestrada on 2010-08-24
go tohttp://www.instructables.com/id/How-to-install-Google-Earth-in-Linux-the-easy-way/;)

---

### Post by alphacrucis2 on 2010-08-25
> **ub9876 said:**
> i got the package and installed..  how to get google earth on desktop  and to run     from terminal..

Easiest to just add the Medibuntu repositories in your software sources and install from there. It will set up a menu launcher for it.

---

### Post by protpisys on 2010-08-25
I got the link as suggested above, got GE in my internet menu but when I click on the icon the program starts for about a second then disappears__ that ain't gppd

---

### Post by wojox on 2010-08-25
> **protpisys said:**
> I got the link as suggested above, got GE in my internet menu but when I click on the icon the program starts for about a second then disappears__ that ain't gppd

If you downloaded 5.2 there is a bug in it now.

Install the one from medibuntu

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

While your add it install some nonfree codecs

```
sudo apt-get install non-free-codecs
```

```
sudo apt-get install googleearth
```

---

### Post by gbestrada on 2010-08-25
If you already installed GE in your machine go to applications > internet > google earth .
to run from the terminal .Open it (terminal). and write home/user/google-earth//googleearth %f.****  U S E R  being your user name ON THE LINE ABOBE ..:D

---

### Post by protpisys on 2010-08-27
that version works, thanks

---

### Post by wojox on 2010-08-27
> **protpisys said:**
> that version works, thanks

Your welcome. Did you have 5.2 installed, the one directly from Google?

---

### Post by JamButty on 2010-09-14
I have the same problem as [protpisys]("http://ubuntuforums.org/member.php?u=1133291"). I installed from the Google site and program pulls these errors on start:

Google Earth could not write to the current cache or My Places file location. The values will be set as follows:
My Places Path: "/home/(username)/.googleearth"
Cache Path: "/home/(username)/.googleearth/Cache"

Those paths/directories are valid. The program starts, offers a tip for less than a second, then crashes.

I would like to follow the suggestions from WOJOX, but I assume I must remove the buggy one I have installed first. That is what I cannot do. Neither Ubuntu Software Center nor Synaptic Package Manager find anything Google installed. I dug around in some dpkg stuff, but that is still pretty opaque for me. The only executable I find is /opt/google-earth/googleearth-bin. There is a shell script - /opt/google-earth/googleearth  also that references the  -bin executable.

So, how do I remove the current package/program before trying to install the one from  medibuntu?
thanks

---

### Post by gandaran on 2010-09-15
> **JamButty said:**
> I have the same problem as [protpisys]("http://ubuntuforums.org/member.php?u=1133291"). I installed from the Google site and program pulls these errors on start:

Google Earth could not write to the current cache or My Places file location. The values will be set as follows:
My Places Path: "/home/(username)/.googleearth"
Cache Path: "/home/(username)/.googleearth/Cache"

Those paths/directories are valid. The program starts, offers a tip for less than a second, then crashes.

I would like to follow the suggestions from WOJOX, but I assume I must remove the buggy one I have installed first. That is what I cannot do. Neither Ubuntu Software Center nor Synaptic Package Manager find anything Google installed. I dug around in some dpkg stuff, but that is still pretty opaque for me. The only executable I find is /opt/google-earth/googleearth-bin. There is a shell script - /opt/google-earth/googleearth  also that references the  -bin executable.

So, how do I remove the current package/program before trying to install the one from  medibuntu?
thanks
look for the uninstall script, cd to the directory in terminal and run it, the uninstall script is in the installation files, if google-earth is installed in root then it will be in /opt or in home user directory if just installed in user account.

---

### Post by JamButty on 2010-09-15
Yes, there is a script 
/opt/google-earth/.manifest/uninstall  (no extension)

Unclear how to run it though. The recommended command from Ubuntu documentation -

sudo bash uninstall

gives 

Could not find a usable uninstall program. Aborting.

with:
sudo uninstall
it treats uninstall as the command, which it does not find.

---

### Post by JamButty on 2010-09-15
File is actually a level up in  /opt/google-earth/

rest of post (errors returned etc.)  is correct. Thanks

---

### Post by JamButty on 2010-09-16
I also tried 
sudo sh uninstall
and tried renaming the uninstall file, thinking there might be some filename vs. command name conflict.

both give the same error -
Could not find a usable uninstall program. Aborting.

Looking over the script, it seems to want a Loki uninstall program. I have no 

HOME/.loki/

directory, so I don't think it is installed. Loki software went out of business in 2001. I find some references to its old uninstall program for Linux, but I can't find anywhere to download it. Also, given that Google Earth is a recent product, I somehow doubt it is using such an old installer/deinstaller, but it is all just guesses for me - I don't really follow the code. The system types it seems to be testing for

"amd64"
"x86"
hppa"
powerpc
don't seem likely, neither "OpenUNIX", because it never displays "SCO_SV"

Anybody familiar with this? Since the shell script is not long, I append it here. thanks.

========================
#! /bin/sh
#### UNINSTALL SCRIPT - Generated by SetupDB 1.6 #####
DetectARCH()
{
        status=1
        case `uname -m` in
           amd64 | x86_64)  echo "amd64"
                  status=0;;
           i?86 | i86*)  echo "x86"
                  status=0;;
           90*/*)
           echo "hppa"
           status=0;;
        *)
        case `uname -s` in
            IRIX*)
            echo "mips"
            status=0;;
           AIX*)
           echo "ppc"
           status=0;;
            *)
            arch=`uname -p 2>/dev/null || uname -m`
                       if test "$arch" = powerpc; then
                          echo "ppc"
                       else
                          echo $arch
                       fi
            status=0;;
        esac
        esac
        return $status
}

DetectOS()
{
  os=`uname -s`
  if test "$os" = OpenUNIX; then
     echo SCO_SV
  else
     echo $os
  fi
  return 0
}

FindBinary()
{
  arch=$1
  if which loki-uninstall 2> /dev/null > /dev/null || type -p loki-uninstall 2> /dev/null > /dev/null; then
    if loki-uninstall -v > /dev/null 2> /dev/null; then
        echo `exec 2>&-; which loki-uninstall || type loki-uninstall`
    else
        echo "$HOME/.loki/installed/bin/`DetectOS`/$arch/uninstall"
    fi
  else
    echo "$HOME/.loki/installed/bin/`DetectOS`/$arch/uninstall"
  fi
}

arch=`DetectARCH`
UNINSTALL=`FindBinary $arch`

# Special case: if amd64 and binary is missing, try to run x86 build...
if test ! -x "$UNINSTALL" ; then
  if test "$arch" = amd64 ; then
    UNINSTALL=`FindBinary x86`
  fi
fi

if test ! -x "$UNINSTALL" ; then
    echo Could not find a usable uninstall program. Aborting.
    exit 1
fi

exec "$UNINSTALL" -L google-earth "/opt/google-earth/.manifest/google-earth.xml" "$1"

---

### Post by gandaran on 2010-09-18
> **JamButty said:**
> Yes, there is a script 
/opt/google-earth/.manifest/uninstall  (no extension)

Unclear how to run it though. The recommended command from Ubuntu documentation -

sudo bash uninstall

gives 

Could not find a usable uninstall program. Aborting.

with:
sudo uninstall
it treats uninstall as the command, which it does not find.
look, its very easy to run that uninstall file if you do it right, fist you have to cd the terminal to the folder that contains the uninstall file then simply type in terminal the run command
```
sudo ./uninstall
```
if you dont know how to cd the terminal then I recommend to install *nautilus open in terminal* from the system repositories, reboot the computer then go to the folder where the uninstall script is, right click the folder and choose open in terminal from the menu then enter the run command.

---

### Post by JamButty on 2010-09-20
```
sudo ./uninstall
```gives the same error as

```
sudo bash uninstall
```I know how to navigate, that is not the problem, neither is the command the problem - something in the code in the script is buggy.
Thanks for trying to help. I will repost as a new topic.

---

### Post by DougieFresh4U on 2010-09-20
If Google Earth is installed, why not go in Synaptic and mark it for complete removal, then apply?

---

### Post by Miljet on 2010-09-20
> If Google Earth is installed, why not go in Synaptic and mark it for complete removal, then apply?

Cause it ain't there? The OP installed directly from the Google site. Therefore it is not registered in Synaptic.

---

### Post by Idiens on 2010-09-23
Thank you Wojox, that worked for me too.

---

### Post by irpsit on 2010-12-24
[B]With this I hope to finish the problem for everyone.
[/B]
To Install Google Earth run these commands:

> sudo apt-get install googleearth-package
(this alone does not install the program!)

> sudo make-googleearth-package --force
(this step takes big time, but it's necessary)

> sudo dpkg -i ./googleearth_5.1.3535.3218+0.5.7-1_i386.deb
(the file name may be different, just browse in /home, or in the last line of the output of last command)

Go to Applications - Internet - Google Earth

If it does not launch, then do

> sudo apt-get install lsb-core

Or you might have to install the following packages:
> sudo aptitude install ttf-dejavu
sudo aptitude install ttf-bitstream-vera
sudo aptitude install msttcorefonts
sudo aptitude install lib32nss-mdns

After this, it should run. But sometimes start-up tips make the software crash
 
So, follow this fix, if Google Earth crashes:  
(applies to Maverick or Lucid)

> gedit ~/.config/Google/GoogleEarthPlus.conf

Now, search for "enableTips" inside the conf file and if it exists, change its value from "true" to "false". If it does not exist, you need to add the following under "[General]" category.

> enableTips=false

Save and Exit. Done. Now try launching Google Earth in Ubuntu, all's going to be fine.

---

