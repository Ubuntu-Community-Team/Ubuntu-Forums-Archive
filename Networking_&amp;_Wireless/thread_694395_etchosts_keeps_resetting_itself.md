---
title: "/etc/hosts keeps resetting itself"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by yellowband on 2008-02-12
what's going on here/  I'm running gutsy with nothing special installed.  I use my wireless card in the laptop to access the internet if that helps.  

I have to make a special entry in my /etc/hosts file for a web development job.  I find that i have to keep re-entering this entry because /etc/hosts has reset itself.  Not sure if the file is reset when I restart the computer or when i switch networks, but its really annoying.  Has anybody seen this before?

---

### Post by diwant on 2008-04-02
Hi,

I was facing the same issue.  In my case I realized that I had different 'locations' configured for my internet settings, and that these settings include entries in the hosts file.

To see your locations settings, left click on the nm-applet icon (The icon that is your internet connection on your panel.  Looks like two monitors for me).  Click on 'Manual Configuration'.  After you type in your sudo password, it will show you a window where there is a combo box on the top labelled 'Locations'.  This is what I am referring to.

To fix your issue, save a location--name it something related to the place where your internet connection is (i.e. home, or home_wireless).  Now go to the hosts tab on that same window, and add your entry(ies) for the hosts file here.  Now save again.  Now everytime it logs onto your home internet using these settings, it will use these hosts entries.

hth,
Diwant

---

