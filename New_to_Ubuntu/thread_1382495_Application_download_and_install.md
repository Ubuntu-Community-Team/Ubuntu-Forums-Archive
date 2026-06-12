---
title: "Application download and install"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by purvis on 2010-01-16
I appologize for being a beginner (and maybe an idiot) but I just can not figure out how to install new software on my computer. I have downloaded a few applications not found in the software store from some various places. After each download completes a nice window pops up showing me all the files that were included in the download. I have been unable to figure out where to go from there. One such example is songbird. Once I have everything downloaded, what do I do with it to make it install and then use it? 
Thank you in advance.

---

### Post by cbabbage on 2010-01-16
The Synaptic package manager is the way to go, it will do everything for you. Go to System > Administration > Synaptic Package Manager. Put in your password, then look through the categories for software you want to install or use the search function to look for a particular package.
The package manager will download and install the package including all dependencies.

---

### Post by Paqman on 2010-01-16
As mentioned above, the Ubuntu repositories are always the first place to go for software. But if you need something that isn't available then your best options are:

[LIST]
[*]Find a PPA with the software available
[*]OR download a .deb file
[/LIST]

PPAs are Private Package Archives, and work like mini repos where community members host pre-packaged software. After subscribing to a PPA you can download through the normal package manager and will get updates whenever they're released.

A .deb file is a simple "download and click to install" package that works a bit like a Windows .exe download.

---

### Post by GROMS on 2010-04-09
> **Paqman said:**
> As mentioned above, the Ubuntu repositories are always the first place to go for software. But if you need something that isn't available then your best options are:

[LIST]
[*]Find a PPA with the software available
[*]OR download a .deb file
[/LIST]

PPAs are Private Package Archives, and work like mini repos where community members host pre-packaged software. After subscribing to a PPA you can download through the normal package manager and will get updates whenever they're released.

A .deb file is a simple "download and click to install" package that works a bit like a Windows .exe download.

How do you go about "subscribing" to a PPA. I want to get the Shutter program as described in Linus Magazine. I'm using Hardey 8.2

---

### Post by jfreak_ on 2010-04-09
just add the name of the ppa to your sources.lst file. The exact command is usually given with the ppa itself

---

### Post by waspbr on 2010-04-09
here is a very easy to use tutorial on how to install software on ubuntu

[http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")

As for songbird, they are going to drop linux support, there is going to be a linux fork named nightingale, though that is going to take some time to come. 

Meanwhile you might want to give banshee a try
[http://banshee-project.org/]("http://banshee-project.org/")

---

