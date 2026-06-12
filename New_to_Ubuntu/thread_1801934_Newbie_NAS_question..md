---
title: "Newbie NAS question."
date: 2011-07-11
forum: New to Ubuntu
---

### Post by highfive on 2011-07-11
Hello.  I'm building a HTPC and decided to try Ubuntu in an effort to break the bonds of MS.  So, I'm a first time Linux user.  The installation went very smooth and so far I like what I see.  But, I am having a problem accessing my Simpleshare NAS drive on my local network.  All my other 4 machines are running WinXP so mapping the drive was easy on those computers. Ubuntu recognized Windows 'Workgroup' but not the NAS server.  I guess I could try assigning static IP's but I'm hoping there is an application that will make the process more automated.  Thanks to all.

:confused:

---

### Post by Jacobonbuntu on 2011-07-11
Hi highfive,

there is a pretty good howto here:
[http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/](http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/)
it works good in my network. if you encounter any problems please let us know!!

P.S and welcome of course!
have a good time, Jacob

P.S. 2
re-reading your post, I see your NAS it not recognized in the WORKGROUP?
try netdiscover first to see if it is in the list of recognized network devices:
to install:
type: sudo apt-get install netdiscover (in a terminal-window)
then: sudo netdiscover

---

### Post by highfive on 2011-07-11
> **Jacobonbuntu said:**
> Hi highfive,

there is a pretty good howto here:
[http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/](http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/)
it works good in my network. if you encounter any problems please let us know!!

P.S and welcome of course!
have a good time, Jacob

P.S. 2
re-reading your post, I see your NAS it not recognized in the WORKGROUP?
try netdiscover first to see if it is in the list of recognized network devices:
to install:
type: sudo apt-get install netdiscover (in a terminal-window)
then: sudo netdiscover

Thank you, Jacob.  Can you recommend a downloadable Ubuntu reference guide (PDF?) that contains commands and syntax?  I haven't worked within Linux for over 10 years (Red Hat) and I've got a learning curve ahead of me. I'm assuming 'sudo' is a derivative of 'su'.  What shells are available? Randy.

---

### Post by Jacobonbuntu on 2011-07-11
Hi again highfive!

If you already have some experience with Linux, you will probably be ahead of me; I am a recent ex Windows / Mac user, used to control my computer with "pictures" :).
I don't know if this is what you mean, but ther is some basic information on the command-line in the (free to download) Ubuntu Pocket Guide and Reference:
[http://ubuntupocketguide.com/download_main.html](http://ubuntupocketguide.com/download_main.html)
I frequently consult the Ubuntu Linux Toolbox (1000+ Commands for Ubuntu and Debian Power users). very good and useful, but I am afraid it is not in pdf.
*edit: how can I forget: [https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto)*

sudo indeed stands for "super user do", to put before every command that requires admin-rights.

Have a good time, hope the NAS will show up :)
Jacob

---

### Post by highfive on 2011-07-12
> **Jacobonbuntu said:**
> Hi again highfive!


....  I frequently consult the Ubuntu Linux Toolbox (1000+ Commands for Ubuntu and Debian Power users). very good and useful, but I am afraid it is not in pdf.  ....


Jacob

Thanks for the info.  FYI, I googled for 'Ubuntu Linux Toolbox PDF' and found several sources.  Very good reference materials.  I'm really impressed with how Linux has evolved.  Now, onto my NAS problem.  Have a good one, Jacob.  Thanks again.  Randy. :)

---

