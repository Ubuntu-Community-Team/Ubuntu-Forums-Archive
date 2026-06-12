---
title: "Installing kdebase-workspace in 9.10 / gnome"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by MrGrumpyArse on 2009-11-04
Hi, before i continue i should explain i am only a week into my Linux adventure so my knowledge is very limited....

I am trying to build/install the latest release candidate of ktorrent (3.3RC1) for the "shutdown plugin" which is if i am correct is only available in this latest release. 
 I have been partially successful but am left with an error in terminal as follows -

 ----------------------------------------------------------------------------
-- The following OPTIONAL packages could NOT be located on your system.
-- Consider installing them to enable more features from this software.
-----------------------------------------------------------------------------
   * libkworkspace  <http://www.kde.org/>
     libkworkspace library and header files
     libkworkspace is needed for shutdown plugin
   * libtaskmanager  <http://www.kde.org/>
     libtaskmanager library and header files
     libtaskmanager is needed for KTorrent Plasmoid

-----------------------------------------------------------------------------

-- Configuring done
-- Generating done
-- Build files have been written to: /home/mark/Downloads/ktorrent-3.3rc1/build
mark@mark-Ubuntu-Beta:~/Downloads/ktorrent-3.3rc1/build$ 

In order to resolve the above i "think" i need to install the package named kdebase-workspace listed in synaptic, but when marking it for install, synaptic lists a whole host  of other packages that will be installed as well.

My questions are really in a nutshell -

Am i selecting the correct package needed to correct the above error?

Is it safe for me to install the package on my pretty much default ubuntu 9.10 / gnome installation? 

If so how will this effect my system from a novice users point of view?

Any advice or information much appreciated

Regards

---

### Post by desperado665 on 2009-11-04
I assume what it wants you to do is load the KDE desktop. It is safe to do, but you should choose the GDM logon manager when prompted. This will allow you to choose between GNOME and KDE sessions when you login.

I have been a Ubuntu user for about 2 years and although GNOME is a great desktop for a beginner, it suffers from a couple of niggles that I found to be a pain. For one, I could never get full screen video to work without tearing unless I disabled compiz first. KDE does this flawlessly. 

I also found the default installation of Kubuntu to be buggy at best, so now I usually start with a default install of Gnome and add the kde-full package, instead of kubuntu-desktop through synaptic. I now use this config with KDE as my default choice on a daily basis.

---

### Post by MrGrumpyArse on 2009-11-04
Thank you for your reply....

After reading your post, a bit more time with google and a visit to the "psycocats" web site which was very informative and has a detailed article about how to install kubuntu on top of ubuntu 9.10 gnome, and just as importantly to me how to remove if you dont like it, i went ahead and installed the kubuntu desktop package from synaptic.

I then tried to do my build/install of ktorrent 3.3rc1 following the instructions on their web site.

Same result, same error :-(  

So having come this far i had another look in synaptic and found that the kdebase-workspace package was not one that was installed along with kubuntu desktop.  This time I went ahead and installed it, then back to terminal to try again with ktorrent........

Success :D everything went fine (to the best of my knowledge) and now i have a working, albeit not really tested ktorrent 3.3 rc1 and the option to log into Kubuntu, which in the brief time i spent on it looks very interesting.

I am posting this back in gnome where everything appears pretty much as was, with the edition of a few apps in the application menu.  So for now I am very happy but I`ll see how things go over the next few days and post again if I encounter any major problems.

Thanks again

A happy MrGrumpyArse

---

### Post by Virtual_Ron on 2009-11-21
I was getting the same error, making Ktorrent3.3
Installing kdebase-workspace didn't fix it.  I had to install kdebase-workspace-dev.

---

