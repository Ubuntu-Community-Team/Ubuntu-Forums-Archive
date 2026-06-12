---
title: "How do i Install Firefox-5.0.1.tar.bz2 On ubuntu9.10?"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by mokman on 2011-07-31
I can install .deb files only.That is how i was able to install  comix404.Plese help me in detail .

---

### Post by sadaruwan12 on 2011-07-31
My dear friend why are you using a very old unsupported version of Ubuntu please upgrade your self to a newer version please.

And to install tar file ok if you have inter net use the PPA packaging it's easy and very safe.

```
    sudo add-apt-repository ppa:mozillateam/firefox-stable
          sudo apt-get update && sudo apt-get upgrade

```

If you have internet this will work like a charm.


For the Tar file

[This might help]("http://www.cyberciti.biz/faq/install-firefox-4-0-tar-bz2-in-linux/") you it's written for FF4 but steps are the same for 5

And this is the [official one]("http://support.mozilla.com/en-US/kb/Installing%20Firefox%20on%20Linux")

---

### Post by trippn740 on 2011-07-31
> **mokman said:**
> I can install .deb files only.That is how i was able to install  comix404.Plese help me in detail .

Are you installing from source? If so, extract the files from the archive; just right click on it and choose "Extract Here."

Go into the extracted directory and first, look for a file named INSTALL (or something similar.) If there's not an installation instruction file, look for a README file. One of those should tell you how to install.

If there are no installation instructions whatsoever; open up the terminal.

Once the terminal is opened, change to the Firefox directory (Firefox-5.0.1) You should be able to type "cd" and drag the folder into the terminal and hit enter. If that doesn't work, (assuming the firefox directory is in your Downloads folder,) type "cd ~/Downloads/Firefox-5.0.1" without the quotes.

Now you're in the right directory. Here is the basic install procedure when installing from source:

```

./configure

make

make check

sudo make install
```

(in that order)

Let me know if it works or not, and if not, post the terminal output (and use code tags!) 

Hope I helped! ;)

---

### Post by linuxman94 on 2011-07-31
> **trippn740 said:**
> Are you installing from source? If so, extract the files from the archive; just right click on it and choose "Extract Here."

Go into the extracted directory and first, look for a file named INSTALL (or something similar.) If there's not an installation instruction file, look for a README file. One of those should tell you how to install.

If there are no installation instructions whatsoever; open up the terminal.

Once the terminal is opened, change to the Firefox directory (Firefox-5.0.1) You should be able to type "cd" and drag the folder into the terminal and hit enter. If that doesn't work, (assuming the firefox directory is in your Downloads folder,) type "cd ~/Downloads/Firefox-5.0.1" without the quotes.

Now you're in the right directory. Here is the basic install procedure when installing from source:

```

./configure

make

make check

sudo make install
```

(in that order)

Let me know if it works or not, and if not, post the terminal output (and use code tags!) 

Hope I helped! ;)

The firefox downloads are not source code, they are already compiled.  

OP: sadaruwan12 is correct.  You should use the ppa and upgrade your system to at least 10.04.

---

### Post by sadaruwan12 on 2011-07-31
Thank you linuxman94

---

### Post by lovinglinux on 2011-07-31
For future reference see [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247")

---

### Post by garvinrick4 on 2011-07-31
#Might as well throw in my ppa or .deb or tarball about same as rest except I threw
in .deb package which you can get in launchpad (upper right of ubuntu forum page) get to
know launchpad is valuable. 
Anytime you can use a "ppa" which is at [http://www.ubuntuupdates.org/ppas](http://www.ubuntuupdates.org/ppas)
use the ppa like stated previously. 
# Can get in a .deb package which is very nice: Download .deb package then:
$ cd path-to-software/
$ ls
$ sudo dpkg -i name of deb package.deb

If have to use tarball below explains:

# 1: Uncompress tarball

To uncompress them, execute the following command(s) depending on the extension:
$ tar zxf file.tar.gz
$ tar zxf file.tgz
$ tar jxf file.tar.bz2
$ tar jxf file.tbz2

Now change directory
$ ls
$ cd path-to-software/

# 2: Build and install software

Generally you need to type 3 commands as follows for building and compiling software:
# ./configure
# make
# make install

Where,

    ./configure will configure the software to ensure your system has the necessary functionality and libraries to successfully compile the package
    make will compile all the source files into executable binaries.
    Finally, make install will install the binaries and any supporting files into the appropriate locations.

# 3: Read INSTALL / README file

Each tarball comes with installation and build instructions. Open INSTALL or README file for more information:
$ vi INSTALL

---

### Post by itagomo on 2011-08-16
if downloaded and extracted the Firefox-5.0.1.tar.bz2, you just need to run the 'firefox' file. No installation/configuration needed. Just add a shortcut to Applications > Internet or to your Desktop.

---

### Post by garvinrick4 on 2011-08-16
If this thread is going to get more action just use "lovinglinux" post and his link
explains it all in detail. POST #6

---

