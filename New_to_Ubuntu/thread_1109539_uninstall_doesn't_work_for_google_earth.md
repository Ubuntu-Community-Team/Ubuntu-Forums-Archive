---
title: "uninstall doesn't work for google earth"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by dondrup on 2009-03-28
i'm totally new to linux as of yesterday!

i have intrepid on AMD 64 and tried installing google earth with the bin from their website. it does say it successfully installed but it crashes as it starts up so i want to uninstall. i found the uninstall icon in the googleearth folder but opening does nothing and it won't open in terminal. how can i get this uninstalled and start afresh?

thanks, stephen

---

### Post by tombom62 on 2009-03-28
open a terminal (I think in ubuntu that is Applications > Accessories > Terminal

Type:
> sudo aptitude remove googleearth
[enter password and confirm that you want to remove it]
and then:
> sudo aptitude purge gooleearth
and to re install:
> sudo aptitude install googleearth
(confirm and wait for download)

thanks,
tombom:popcorn:

---

### Post by HermanAB on 2009-03-28
Google earth is terrible software - it doesn't work properly - if at all.  To remove it, figure out where it was installed to (probably /usr/local) and delete it.

There are other services provided by the government geological services of many countries that are much better than Google Earth.

For example: [http://atlas.nrcan.gc.ca/site/english/maps/topo](http://atlas.nrcan.gc.ca/site/english/maps/topo)

---

### Post by ranch hand on 2009-03-28
Just out of curriousity; what did you install exactly?  And how?

I am wondering if you "installed" an .exe file.  This will not work on a linux system.

Click on folder to highlight and hit delete if this is the case.

I have not fooled around with google earth as dial up is not the best connection for it but I do believe there is a version for linux.

I have never seen a linux program with an uninstall option al though there may be such an animal that my limmited experience has missed.

---

### Post by tombom62 on 2009-03-28
> **HermanAB said:**
> Google earth is terrible software - it doesn't work properly - if at all.  To remove it, figure out where it was installed too (probably /usr/local) and delete it.

There are other services provided by the government geological services of many countries that are much better than Google Earth.

For example: [http://atlas.nrcan.gc.ca/site/english/maps/topo](http://atlas.nrcan.gc.ca/site/english/maps/topo)

Google earth is good and it's what he wants.  I had that problem too and I just fixed it with that so I posted it.  And to get rid of google earth, do my 1st 2 terminal steps, and to re insntall it do the 3rd as well.

thanks,
tombom:popcorn:

---

### Post by jmszr on 2009-03-28
dondrup,

          This might help you out: [http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/](http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/)

---

### Post by ranch hand on 2009-03-28
I just checked and it is available through synaptic.

To be safe and get things installed correctly you should stick to apts available through the repositories these can be installed with synaptic, apttitude, apt get or add/remove.

---

### Post by ranch hand on 2009-03-28
As one newby to another; read this:
<http://linux.oneandoneis2.org/LNW.htm>

---

### Post by mvalviar on 2009-03-28
Yet another GE problem. I wish someone make a sticky on this. 

****If installed using bin file. If you install without sudo ```
cd ~/google-earth
./uninstall
```. If you install with sudo ```
cd /opt/google-earth
sudo ./uninstall
```

****If installed using apt-get/synaptic```
sudo apt-get autoremove googleearth
```

---

### Post by dondrup on 2009-03-29
still no luck.

With regards to tombom's suggestion:

this is the result so i didn't try the next steps of purging and reinstalling.

$ sudo aptitude remove googleearth
[sudo] password for dondrup: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Couldn't find package "googleearth".  However, the following
packages contain "googleearth" in their name:
  googleearth-package 
Couldn't find package "googleearth".  However, the following
packages contain "googleearth" in their name:
  googleearth-package 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

and here is the result of mvalviar's code [i installed with sudo]:

~$ cd /opt/google-earth
dondrup@sman:/opt/google-earth$ sudo ./uninstall
Could not find a usable uninstall program. Aborting.
dondrup@sman:/opt/google-earth$ 

then i tried the tombuntu suggestions
[http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/#comment-55511](http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/#comment-55511)
...but i don't have permissions to change the libcrypto.so.0.9.8 file name so i'll try to figure out how to do that.

thanks for the replies. i am impressed with friendliness here!

by the way i opened the little uninstall icon that won't work and here is the text inside [it won't run or open in terminal]:

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

### Post by ranch hand on 2009-03-29
Get rid of that file and try the install through aptitude, apt-get or synaptic again.

Just right click on the file and delete.

---

### Post by dondrup on 2009-03-29
thanks, i figured out how to change permissions and addded .bak to libcrypto.so.0.9.8 and now it works [except for lots of flickering]

---

