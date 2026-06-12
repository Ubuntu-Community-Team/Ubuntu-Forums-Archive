---
title: "How do I fix these dependency problems?"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by lawrencegoodman on 2010-06-23
I am getting the following error msgs when I try to install a new program:

> E: gconf2-common: subprocess installed post-installation script returned error exit status 10
E: libgconf2-4: dependency problems - leaving unconfigured
E: libbrasero-media0: dependency problems - leaving unconfigured
E: brasero: dependency problems - leaving unconfigured
E: libedataserver1.2-11: dependency problems - leaving unconfigured
E: libcamel1.2-14: dependency problems - leaving unconfigured
E: libebackend1.2-0: dependency problems - leaving unconfigured
E: libebook1.2-9: dependency problems - leaving unconfigured
E: libecal1.2-7: dependency problems - leaving unconfigured
E: libedata-book1.2-2: dependency problems - leaving unconfigured
E: libedata-cal1.2-6: dependency problems - leaving unconfigured
E: libegroupwise1.2-13: dependency problems - leaving unconfigured
E: evolution-data-server: dependency problems - leaving unconfigured
E: libedataserverui1.2-8: dependency problems - leaving unconfiguredunconfigured
E: gstreamer0.10-plugins-good: dependency problems - leaving unconfigured
E: libgnomekbd-common: dependency problems - leaving unconfigured
E: libgnomekbd4: dependency problems - leaving unconfigured

I have tried apt-get upgrade and apt-get install -f with no luck.

Thanks.

---

### Post by viralmeme on 2010-06-23
> **lawrencegoodman said:**
> I am getting the following error msgs when I try to install a new program: I have tried apt-get upgrade and apt-get install -f with no luck.
What's the name of this program you are attempting to install. What version of Ubuntu are you using?

---

### Post by Thelasko on 2010-06-23
Did you manually edit any configuration files used by gconf2-common?

Try "sudo apt-get -purge gconf2-common" and reinstall

---

### Post by lawrencegoodman on 2010-06-23
I am using Lucid Ubuntu.

I made no changes to any configuration files as far as I know.

I would uninstall gconf2-common but doing so will remove dozens of other packages on my system. Isn't there any other way?

Thanks.

---

### Post by lawrencegoodman on 2010-06-23
Not sure if it's relevant but I am also getting these error msgs when I install via apt0get on command line:


> dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of f-spot:
 f-spot depends on gconf2 (>= 2.10.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing f-spot (--configure):
 dependency problems - leaving unconfigured

---

### Post by doas777 on 2010-06-23
did you guys uninstall any components of the ubuntu-desktop package? 

my life with ubuntu got much easier once I started ignoring packages I don't use rather than trying to uninstall them. 

you can try:
```

sudo apt-get install ubuntu-desktop

``` to replace any missing components of the package. hopefully after that, all depends will be met.

---

### Post by Thelasko on 2010-06-23
> **lawrencegoodman said:**
> 
I would uninstall gconf2-common but doing so will remove dozens of other packages on my system. Isn't there any other way?

Try
```
sudo apt-get --reinstall gconf2-common
```

Unfortunately, this won't fix any broken configuration files if that is the problem.

---

### Post by lawrencegoodman on 2010-06-23
It says I am using the latest version of gnome-desktop. When I try to reinstall, it says this:


Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ekiga: Depends: libopal3.6.8 but it is not installable
         Depends: libpt2.6.7 but it is not installable
E: Broken packages

---

### Post by da burger on 2010-06-23
Please tell us the name of the package you are trying to install. That gives us a much better start in trying to solve your problem.

---

### Post by Thelasko on 2010-06-23
Well, I have an idea, but I don't know if it will work.  I've never tried this before on any program other than xorg.

```
dpkg --configure gconf2-common
```

I'd call it risky.  If anyone else has a suggestion, I'm open to hear it.

---

### Post by Paqman on 2010-06-23
> **lawrencegoodman said:**
> 
The following packages have unmet dependencies:
  ekiga: Depends: libopal3.6.8 but it is not installable
         Depends: libpt2.6.7 but it is not installable
**E: Broken packages**

Open up Synaptic and see if you have any broken packages listed.

---

### Post by lawrencegoodman on 2010-06-23
It happens with every package I try to install.
I tried checking Synaptic a long time ago, and it doesn't indicate I have any unmet dependencies.

I notice that gnome-desktop-environment is not installed on my system. I go to install it though and it says I need ekiga, but when I try to install ekiga, I get:


ekiga: Depends: libopal3.6.8 but it is not installable
         Depends: libpt2.6.7 but it is not installable

---

### Post by oldos2er on 2010-06-23
Have you run **sudo apt-get update** lately?

---

### Post by anewguy on 2010-06-23
Whatever the initial package was you were trying to install - for the sake of this example we'll call it package1 - try:

sudo apt-get build-dep package1

The build-dep option is supposed to grab all the dependencies for the given package.

As another example, for the gnome desktop, try:

sudo apt-get build-dep gnome-desktop-environment

then

sudo apt-get install gnome-desktop-environment




Dave ;)

---

### Post by elboulangero on 2012-03-05
I had the same troubles lately, after I mistakenly uninstalled gnome. I couldn't install libpt anymore.

In the end I found that the problem was my */etc/apt/sources.list*. I found that libpt2.6.7 doesn't exist in the Debian SID repository for my architecture. So I just added the wheezy  repository to my sources.list, and it worked.

Well you're using Ubuntu, but maybe there is the same problem. Check your sources.list !

---

### Post by oldos2er on 2012-03-05
Closed, necromancy.

---

