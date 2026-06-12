---
title: "problems with ./configure"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by Crash.hm on 2009-03-03
I've tried using ./configure to start installs from tar balls but i keep getting this error messages. 

{configure: error: C compiler cannot create executables
See `config.log' for more details.}

what am I doning wrong?

---

### Post by ddixonr on 2009-03-03
If you followed these steps as well, I'm out:

tar xzvf ABC.tar.gz
cd ABC
./configure
make
sudo checkinstall

---

### Post by oldos2er on 2009-03-03
Install the package build-essential

---

### Post by Crash.hm on 2009-03-03
whats a package build?

---

### Post by ddixonr on 2009-03-03
Type this into a terminal: sudo apt-get install build-essential

---

### Post by sgosnell on 2009-03-03
You get the essential elements necessary to build an app, including a compiler, make, and everything else.  Why build-essential is not included in the distribution, I can't say.

---

### Post by ad_267 on 2009-03-03
Also a bit of a heads up, usually you'll get errors when running configure if you don't have a required dependency and you'll have to install these packages. You have to make sure you get the development packages too (the ones that end in -dev).

---

### Post by Crash.hm on 2009-03-04
> **ad_267 said:**
> Also a bit of a heads up, usually you'll get errors when running configure if you don't have a required dependency and you'll have to install these packages. You have to make sure you get the development packages too (the ones that end in -dev).

could you explain the development packages?
so far programs have asked me to load stuff like bison and m4. I'm starting to make progress... My computer is crashing :) i think its just getting over taxed and i'm probably pissing it off ./comfigure and not doing some sort of memory dump between attempts

---

### Post by ad_267 on 2009-03-04
The -dev package thing doesn't apply for bison and m4, but it does apply for many other libraries. One example could be gtk. You will already have the libgtk2.0 package installed because many applications depend on this to run. But if you want to compile a gtk application you also need libgtk2.0-dev. This package contains the gtk header files and static libraries.

Your computer shouldn't really be crashing just from running a configure script, and there's no memory dump or anything else you should be doing.

---

### Post by jaminux on 2009-03-04
When you download a tarball make sure to check the dependencies in the readme or on the website.

Search for them in the synaptic. They will either be called by their name or lib something or other. E.g. if the documentation said awk I would search for awk and libawk to see whether I had got everything.

In addition you want any header files, ending with the name -dev for each package. For example, awk-versionxyz-dev. 

Oh and remember to check you have the right VERSION as well. If you do not you will have to get a more recent one, either by trying to find a deb on the web or by installing the package from source.

not 100% sure about the exact details of the next bit so please correct me if I am wrong

the configure script configures the application for compiling and checks prerequisites. If you get an error at this stage you probably don't have the right applications installed.

the make stage compiles the program for you. Compiling is the process of human-readable code being converted into a format that the machine can understand (exclude Java from this equation). If you get an error at this stage it is probably to do with the code being built wrong or being incompatible with your compiler (e.g. uses very new features). If something goes wrong at this point you cannot really do much.

finally sudo make install installs the compiled code into the correct place on your system. Remember to put the sudo or you will get an error message.

Hope that helps

---

### Post by jaminux on 2009-03-04
> **Crash.hm said:**
> could you explain the development packages?
so far programs have asked me to load stuff like bison and m4. I'm starting to make progress... My computer is crashing :) i think its just getting over taxed and i'm probably pissing it off ./comfigure and not doing some sort of memory dump between attempts

Dev files are files containing headers. Don't ask me exactly what that means as I don't know. As far as you and I are concerned though it basically means you need them if you want to compile from source.

---

### Post by andrew.46 on 2009-03-04
Hi,

Can I ask which application you are trying to compile?

 Andrew

---

### Post by Crash.hm on 2009-03-07
i was trying to compile bison because claws asked for it

---

### Post by ad_267 on 2009-03-08
Bison is available from the Ubuntu repositories. You can install it with "sudo aptitude install bison" or form System - Administration - Synaptic Package Manger. See [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) for more information on installing software in Ubuntu.

---

