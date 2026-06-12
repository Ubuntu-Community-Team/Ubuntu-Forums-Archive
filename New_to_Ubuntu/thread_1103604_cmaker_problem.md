---
title: "cmaker problem"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by recycledhippy on 2009-03-22
I tried to run cmaker and I get a error that says

CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
CMake Error: Internal CMake error, TryCompile configure of cmake failed
-- Check for working CXX compiler: CMAKE_CXX_COMPILER-NOTFOUND -- broken
CMake Error at /usr/share/cmake-2.6/Modules/CMakeTestCXXCompiler.cmake:25 (MESSAGE):
  The C++ compiler "CMAKE_CXX_COMPILER-NOTFOUND" is not able to compile a
  simple test program.

  It fails with the following output:

   

  

  CMake will not be able to correctly generate this project.
Call Stack (most recent call first):
  CMakeLists.txt:3 (PROJECT)


CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
-- Configuring done


any help would be great!!!

---

### Post by ibuclaw on 2009-03-22
Do you have g++ installed?

```
sudo apt-get install build-essential
```

Regards
Iain

---

### Post by recycledhippy on 2009-03-22
it appears maybe I didn't. Ill try cmaker again and let you know.

---

### Post by recycledhippy on 2009-03-22
it seems not all is good. Ineed to install something(see below) do you know how I ccan go about doing that? And how do I remove the cmakecache txt?







CMake Error at CMakeLists.txt:118 (MESSAGE):
  LMMS requires libsndfile1 and libsndfile1-dev >= 1.0.11 - please install,
  remove CMakeCache.txt and try again!

---

### Post by snova on 2009-03-22
> **recycledhippy said:**
> LMMS requires libsndfile1 and libsndfile1-dev >= 1.0.11 - please install,

Install the **libsndfile1-dev** package, however you want. Quickest way through the terminal is:

```
sudo apt-get install libsndfile1-dev
```

> remove CMakeCache.txt and try again!

Well, find the file and remove it. :) It should be in the current directory; wherever you're building it at.

```
rm CMakeCache.txt
```

---

### Post by recycledhippy on 2009-03-22
thanks for the help looks like I have another problem I have to figure out. I wish installing thing was easier in ubuntu!

---

### Post by snova on 2009-03-22
> **recycledhippy said:**
> thanks for the help looks like I have another problem I have to figure out. I wish installing thing was easier in ubuntu!

It usually is. But compiling from source can be complicated, since there are no rules such downloads need abide by. They come in all shapes and sizes, plus you need to have various dependencies installed first.

Unless you know you need to build LMMS from source, is there any particular reason you cannot install from the repositories?

Open System -> Administration -> Synaptic; then search for and install 'lmms'. And that should be it.

---

### Post by recycledhippy on 2009-03-22
it's not the newest version. How can I go about getting the newest version?

---

### Post by snova on 2009-03-22
> **recycledhippy said:**
> it's not the newest version.

Good enough for me. :)

> How can I go about getting the newest version?

On their [download page]("http://lmms.sourceforge.net/download.php"), I see they offer binaries for Ubuntu. It's a [PPA]("https://launchpad.net/~tobydox/+archive/ppa").

Now, adding a PPA is a slightly drawn-out process, but in the end it's much simpler than compiling from source. The instructions are [here]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories").

First, we add the repository to your sources list. Open System -> Administration -> Software Sources (or similar, I forget what it's called). Go to the Third-Party Software tab, press Add, and paste this in:

```
deb http://ppa.launchpad.net/tobydox/ppa/ubuntu intrepid main
```

Download [this]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x02FE5F12ADDE29B2") file and save it somewhere. Go to the Authentication tab, press Import Key File and select the file you just downloaded.

Then close the window. It should prompt for you to reload, do so.

Then you should be able to open Synaptic and install the latest version of LMMS from it. It should automatically update itself with new releases, too.

---

### Post by recycledhippy on 2009-03-23
I got to the download the key file but your link is not a download its a page. how to I go about saving it? or is this the right thing?

---

### Post by recycledhippy on 2009-03-23
k nevermind I think I got it but there is no updated version in Synaptic

---

