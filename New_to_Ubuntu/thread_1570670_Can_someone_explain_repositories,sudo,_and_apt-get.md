---
title: "Can someone explain repositories,sudo, and apt-get?"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by cheetos316 on 2010-09-08
Newb question here but can someone explain what they are and how they work?  I'm pretty new to Linux and want to understand it more.  I used to love using MS-DOS and still hate using the mouse so I would like to learn more about terminal commands.

My guess is that repositories are programs that are on the Ubuntu server.  But if that is the case, how do we access it or see what is available for use?

sudo - seems like a command that is used to gain access to root, but why have such a command?  If it is to protect users from doing a lot of damage, couldn't everyone use it anyways?

apt-get - I'm pretty confused by this one.  Seems like it is used to install programs.  Are these programs already in the distro or is it that everytime it is used, the OS has to download it?  If so, what happens if there is no internet access?

Feel free to share anything else that is interesting!

Thanks!

---

### Post by CharlesA on 2010-09-08
Repositories are just collections of software packages.

You use sudo to run something with superuser privlages - aka root. By default only those in the administrator group have access to sudo.

apt-get is a package installer, it pulls stuff from the repos and installs them. It downloads the packages over the internet, so if you don't have internet access you won't be able to install packages.

However you can use AptonCD to download and keep offline copies of repositories.

---

### Post by inameiname on 2010-09-08
In addition to CharlesA's comments, 

Repositories are just where you get the software. Ubuntu itself has repositories, which is like a server full of packages, in which you can use apt-get (or a similar, if not better equivalent to apt-get, apititude) can search, install, remove, whatever from those repositories. Ubuntu's repos are the official ones. On the net there are tons of other non-official ones, some called PPAs, from [www.launchpad.net]("http://www.launchpad.net"), which are users' extras they've compiled and made (either for experimenting with test versions of packages, or because the official Ubuntu repos tend to get outdated), and some are repos from other websites, like that of Remastersys (a Linux custom cd backup god). 

And of course, you require administrative priviledges to be able to use apt-get for installing and upgrading packages, which is achieved by 'sudo' use.

To see what's inside a repository, there are a number of ways. You can search for a specific package through 'sudo apt-cache search (package name)', which can be hard if you don't know the name of something, use the Synaptic Package Manager, which is like a gui for apt-get, or use the Ubuntu Software Center. Currently, the Lucid Ubuntu Software Center for Lucid kind of sucks, but you can search for software the easiest there. In Maverick, (or if you add a PPA with the latest Ubuntu Software Center), you can get the latest version that is really cool. It'd be the best way for a newbie to view packages.

So unlike Windows, which other than what comes pre-installed, you must search the net for applications you want and download them from their websites, repositories already have put together a large collection of applications they've deemed worthy to include inside their repositories, so all you have to do is search for and find them, and then can install them with a simple apt-get command. One thing Linux beats Windows over by far.

---

### Post by bbqsandwich on 2010-09-08
> **cheetos316 said:**
> sudo - seems like a command that is used to gain access to root, but why have such a command?  If it is to protect users from doing a lot of damage, couldn't everyone use it anyways?

To run a command as superuser (sudo) you have to know the password, so no, not everyone could use it anyways. ;)

---

### Post by drs305 on 2010-09-08
Here's the Ubuntu community doc on Repositories, which provides a general overview:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by candtalan on 2010-09-08
> **cheetos316 said:**
>  My guess is that repositories are programs that are on the Ubuntu server.  But if that is the case, how do we access it or see what is available for use?  Speaking loosely here: Repositories are, in non computer speak, like book libraries only they contain programs or packages of program items. A repository, (repo) is guarded (administered) by a group or organisation. The easy way to manage the basics is by
System>Administration>Software sources 
I think.

Repos come in different flavours. The inner sanctum for Ubuntu is the repos administered and verified as good, by the Ubuntu central team. Other repos such as universe and the wider multiverse contain things which have a more distant provenance, but may still be excellent for your purpose. A popular repo is medibuntu.

>  sudo - seems like a command that is used to gain access to root, but why have such a command?  If it is to protect users from doing a lot of damage, couldn't everyone use it anyways? 
I think of sudo command as being an abbreviation of a phrase like 'super user doing something'. A specific something that is. The reason to have and use it is so that while it is secure to run (a GNU/Linux) OS as an ordinary User, it is inherently not secure in a wider sense, to run while logged in as root (super user). When, or if, you are logged in as root, then anything can be done, anything at all. Actions are unrestricted. mistakes can be disaster. Any other processes can also use the root privileges because there are no boundaries. If one of those processes happens to be malware, it then has free reign.

The sudo command allows a certain user to attain root privileges for a certain limited list of actions. For the user, in a listed action, the privilege is full root, but is limited and is not system wide.
GNU/Linux distros such as Ubuntu do not even have a root account to be logged into. Although it is not difficult for an experienced user to create one. But then such a user is unlikely to WANT such an account.


> 
apt-get - I'm pretty confused by this one.  Seems like it is used to install programs.  Are these programs already in the distro or is it that everytime it is used, the OS has to download it?  If so, what happens if there is no internet access?
Feel free to share anything else that is interesting!
Thanks!

I leave these for others to elaborate upon, time is short here just now, sorry.
hthg

---

### Post by philinux on 2010-09-08
For info on your questions and more.

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by mapes12 on 2010-09-08
From the other posts I guess you get the idea of the answers to your questions. 

Just to add my bit. In the windoze world you browse the web and find an application you like the look of. You download an .exe file, launch it and think "all is well" because the app works. But what you _don't_ know is what the app has installed that you can't see and may be malicious to your system.

On the other hand, with repos, you have a choice of vetting what repos you enable on your system. For example, if you only enable the Ubu repos you know that every single app is vetted, examined and vetted again by a community that do not want and will not allow malicious apps into the repo. Open source allows this to function.

If you enable repos that are out of scope of community vetting then there are risks.

You are in control (unlike the world of .exe files)

If you like Ubu (and it takes a while to climatise) then stay with it. It's fast, safe, and has a great helpful community to help you along.

Mark

---

### Post by beew on 2010-09-08
maples12

> On the other hand, with repos, you have a choice of vetting what repos you enable on your system. For example, if you only enable the Ubu repos you know that every single app is vetted, examined and vetted again by a community that do not want and will not allow malicious apps into the repo. Open source allows this to function.

Yes, but softwares in the Ubuntu repo also tend to be outdated and some ridiculously so because of the feature freeze. That means they don't update softwares in the repo for 6 months except for security patches and bug fixes(?), but no new features. And if you want new stuffs after 6 months you need to upgrade the whole OS. So, no, you are not in that much control if you stick to the official repo, the OS has more control. :)

Now of course some programs evolve slowely and a newer release are not much different. But others are adding more features and improvements in very rapid pace and the official repo version can get very stale. Security and stability comes at a cost that I think new users should know.


To remedy this one can enable third party repositories known as PPA which tend to be more updated.[https://help.ubuntu.com/community/Repositories/CommandLine#Adding Launchpad PPA Repositories]("https://help.ubuntu.com/community/Repositories/CommandLine#Adding Launchpad PPA Repositories") You can also add PPA easily through Synaptic. Usually the webpage that hosts the PPA would ask you to cut and paste a line to Synaptic with some  (easy) instructions.

I use PPA's for end user applications but not for system things as those can be risky. The OP may also want to get Ubuntu tweak (there is a PPA in their repo, google it)It has a neat feature called PPA purge, in case problems arise with some packages in the PPA's it would be able to downgrade the packages and remove the problematic PPA safely.

P.S. The OP can of course also download .deb files (like windows' .exe installers which one installs by clicking) or a tarball and build from source (not for beginners) but programs installed these way have to be updated manually instead of through the program manager like programs in Ubuntu repos (they do get security updates) or PPA's.

---

### Post by philinux on 2010-09-08
beew,

That's where the backports repo comes in.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by beew on 2010-09-08
> **philinux said:**
> beew,

That's where the backports repo comes in.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Only theoretically, it is not used very much. Take a look at the list of programs in the backport, it is very limited.

---

### Post by philinux on 2010-09-09
> **beew said:**
> Only theoretically, it is not used very much. Take a look at the list of programs in the backport, it is very limited.

[http://packages.ubuntu.com/lucid-backports/allpackages](http://packages.ubuntu.com/lucid-backports/allpackages)

But it is useful.

---

### Post by beew on 2010-09-09
phillinux

I knew the list, hence my reply. Look at what you get in there. The only thing that is interesting for my purpose is virtualbox but I am  using the close version (need usb support) rather than ose. I don't use clamav and since most Linux users don't use any av that is kind of moot (aside: if you do need an av at least  get something decent clamav is a garbage) I have no use for all the kde stuffs and that are pretty much all of the repo and there are some libraries which may be useful but they are not applications.

---

