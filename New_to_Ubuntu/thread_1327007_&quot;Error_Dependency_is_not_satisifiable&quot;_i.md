---
title: "&quot;Error: Dependency is not satisifiable&quot; issues"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by kudzu on 2009-11-15
Hey guys,

I'm coming back to Ubuntu after installing it and using it briefly, and then going a year or so without using it.  I'm trying to get back into it now, and I'm trying to install Nate On Messenger, along with its Pidgin plug-in, but I get different "Error: Dependency is not satisfiable" messages for each one.  

When I try to install the Nate On .deb file (nateon-1.0_204-1_i386.deb) I get "Error: Dependency is not satisfiable: libgcrypt11"  So, I did some research and came to the conclusion that I needed to install libgcrypt11 before installing Nate On, but I checked and I already have libgcrypt11 installed.  So I reinstalled it - didn't help.  I installed every libgcrypt11 variant in Synaptic - didn't help.

I have a similar situation with the Nate On Pidgin plug-in (pidgin-nateon_0.0.0.svn136-1_i386.deb), except instead of libgcrypt11 being the issue it's libpurple0.  Like the other situation, though, I already have that file installed, and I went ahead and installed every libpurple0 variant in Synaptic.

I'm using Ubuntu Hardy Heron 8.04, and as far as I can tell it is up to date.

Thanks.

---

### Post by Paqman on 2009-11-15
Your problem might be that the packaages you're trying to install require you to not just have certain packages, but certain *versions* of those packages.

Hardy is quite old, and doesn't have the required packages in the repos. There is a PPA available for the [NateOn Pidgin plugin]("https://launchpad.net/~pidgin-nateon/+archive/ppa?field.series_filter=hardy"). If you add that PPA to System > Admin > Software Sources you'll be able to get the plugin from Synaptic. 

There appears to be a PPA [here]("https://launchpad.net/~ubuntu-ko/+archive/ppa?field.series_filter=hardy") that includes the NateOn client for Hardy.

---

