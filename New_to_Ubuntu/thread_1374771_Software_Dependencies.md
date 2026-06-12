---
title: "Software Dependencies?"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by Scooter_X on 2010-01-07
Why is it that in many occasions when i want to download what would seem like a basic thing, I'm always told that I need to also download X Y and Z bits and pieces of software because the program I want is dependent upon them? It seems a hassle and if you don't know specifically what you're doing, downloading and installing things can be a big pain in the neck!!

I would imagine that all that stuff could be wrapped up in the same package and when installing, it could check for those things and if they are present it just skips installing them, and if not, then they install.

Any light that can be shed on this would be appreciated. Thanks a lot! :D

---

### Post by howefield on 2010-01-07
If you are installing from the official repositories, all the dependancies will be taken care of for you. It really isn't a problem.

Do you have a specific issue in installing a specific application, if so, what is it ?

---

### Post by theDaveTheRave on 2010-01-07
> **howefield said:**
> If you are installing from the official repositories, all the dependancies will be taken care of for you. It really isn't a problem.


Indeed.

If you are grabbing stuff that has been bundled up in a < deb > repository I believe that the system should also check for dependencies in this case too.

However if you are installing from source, you may need to check to see what dependencies are required.

You may also find that a package in source may have a script that is specific for debian instalations.

The advantage is that you don't accidentally download multiple copies of the same dependencies, which can often be the case with windows. There and installer will often carry copies of the required depencies, and install them in a separate location. Ultimatly causing problems with the path when the system finds the same thing (or worse the same thing in different versions) in 2 locations.

I admit it can be a fiddle. But then, it also means you can avoid having stuff you don't need.

for instance.

Windows seems to be reliant on an instalation of internet explorer (or parts of it) for getting the windows security updates. Why they can't just use an ftp call I don't know? But IE is impossible to delete because of this, even though you are only using a small "subset of it's abilities".

In the linux world everything is much more <modular>. If you need a certain tool, you go and use one already available, unless you specifically have a reason to create a new one (such as it is often more fun to roll your own!).

Hope this helps, if you are having problems with a specific package however like howefield says, try a search on the forum for that.

good luck

David

---

### Post by Scooter_X on 2010-01-07
@howefield- no specific ones, but for example I was just thinking about when I was trying to install a different chat client that uses the MSN protocol I went to their specific websites, and some of them were like that where I had to dig up the dependencies on my own and figure out how to install them. But then eventually I figured out "oh yea, the ubuntu software center may have it" and sure enough, I found several.

@Dave- Thanks a lot for that about Windows and it's program dependencies. I never would've even thought of that. It helps to understand that both OS's are the same in that aspect, but that with Linux I can better manage it.  It helps also to know what kinds of packages/files to look for when I don't feel like digging around for dependencies. By <deb> we refer to 'debian'?

Now, by 'repository' we mean basically just a package deal that should have and be able to install any required dependencies, right?  (I previously just thought that it was a place I could go to find other software.)

Thanks for the help guys. Really appreciated.

---

### Post by Paqman on 2010-01-07
> **Scooter_X said:**
> 
I would imagine that all that stuff could be wrapped up in the same package and when installing, it could check for those things and if they are present it just skips installing them, and if not, then they install.


That's pretty much what your package manager does.

When you ask to install a package, the package manager checks to see if you already have the dependencies. If not, it downloads them. If you already have them, it doesn't.

The end result is that you only ever download exactly what you need. It's a much more efficient system than you'll get on Windows or Mac.

---

### Post by Methuselah on 2010-01-07
Up-to-date tutorial that covers Software Centre:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Older but still applicable: How to install anything in Ubuntu
[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

Most times you do not need to download software from various websites directly.
People who formerly used windows often have a hard time getting used to this concept.

Many times websites give very generic versions of linux applications and you'll have to do all the legwork to get it working with the particular distribution you are using.
But chances are good that the program you want is already packaged for Ubuntu and is available at your fingertips in the Software Centre or Synaptic.

---

### Post by 3rdalbum on 2010-01-07
> **Scooter_X said:**
> I would imagine that all that stuff could be wrapped up in the same package and when installing, it could check for those things and if they are present it just skips installing them, and if not, then they install.

What would be even cooler is if all the dependencies were in different packages, and when installing it could check for those things; and if they are not present then they are downloaded and installed. It would save bandwidth to not have to download libraries and stuff that you already have.

Oh hey, that's already what happens!

But seriously, there's a good reason why libraries are not included as part of the program (unless they are obscure). If there's a security flaw found in a library, then Ubuntu can push out an updated version that will fix ALL software that requires that library, and the software developers who use that library won't have to lift a finger.

Re-downloading seven different programs because a single library has changed, really sucks.

---

### Post by slakkie on 2010-01-07
> **Scooter_X said:**
> @howefield- no specific ones, but for example I was just thinking about when I was trying to install a different chat client that uses the MSN protocol I went to their specific websites, and some of them were like that where I had to dig up the dependencies on my own and figure out how to install them. But then eventually I figured out "oh yea, the ubuntu software center may have it" and sure enough, I found several.


You have to worry about dependencies when you install from source, which apt can do for you: apt-get build-dep <package>. It will then install all the build dependencies for that package so you can compile it from source. If the package is not known then you might do some digging yourself (but you have a log which says which packages you need, so...).

> 
@Dave- Thanks a lot for that about Windows and it's program dependencies. I never would've even thought of that. It helps to understand that both OS's are the same in that aspect, but that with Linux I can better manage it.  It helps also to know what kinds of packages/files to look for when I don't feel like digging around for dependencies. By <deb> we refer to 'debian'?


A deb is a software package in Debian format. Ubuntu uses .deb's as wel. Red Hat and other RPM based systems use RPM, which means RedHat Package Manager (although "renamed" too RPM Package Manager).

> 
Now, by 'repository' we mean basically just a package deal that should have and be able to install any required dependencies, right?  (I previously just thought that it was a place I could go to find other software.)


No, a software repository is a source where we get packages from. A repository does not necessarily include all the dependencies for a particular package which is offered via that repository. Eg, my PPA has a package which depends on python2.5 but I don't provide it. You need to have the official repositories (or others) which do include them. 
 
Google offers Chrome via a repository, but also doesn't offer the dependencies, it let's Debian/Ubuntu take care of those packages.

---

### Post by Scooter_X on 2010-01-07
Yes! Loads of great information. Thanks everyone tons. I just want to do a quick recap so I make sure that I understand:

the Package Manager is for finding those dependencies. When I get a .deb file, it works with the Package Manager to make sure I have them. If not, it's the Package Manager's job to download and install them.

If I want to compile from source, I can use "apt-get build-dep <package>" to install the packages (dependencies) that I need. (The packages are often listed on the websites, I need to plug in the file name where it says <package>)

And then Ubuntu's Synaptic Package Manager then updates those packages when and if necessary 

Do I have it right?

---

### Post by Scooter_X on 2010-01-07
Okay, I'll just assume that I got it right. It makes sense at any rate.

---

### Post by Paqman on 2010-01-07
> **Scooter_X said:**
> 
the Package Manager is for finding those dependencies. When I get a .deb file, it works with the Package Manager to make sure I have them. If not, it's the Package Manager's job to download and install them.


When people say "the package manager" they actually mean dpkg/APT. That's the system that works behind the scenes installing, upgrading and removing all software on your Ubuntu system.

Whenever you use Software Centre, Update Manager, Synaptic, apt-get or Gdebi (the gizmo that installs .deb files) then you're actually using APT. Whenever you install a package the package manager compares what's on your system to the repos and downloads the extra bits you need. Whenever updates for any of those components hit the repositories, it will get the updates for you and install them. Because of this your whole system should always be right up to date, which is really important for security. 

Operating systems which don't have package managers (eg: Windows, OS X) aren't able to update the whole system this way, and have to use a whole bunch of separate updaters that don't talk to each other. A lot of their apps just don't update themselves at all.

Package managers are IMO the single best thing about using Linux.

---

