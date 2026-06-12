---
title: "i need help with something, about how computers behind the same routedr interact"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by hyperhopper on 2009-06-10
my dad thinks that if i have alot of tabs open in firefox, this will slow him down since we are behind the same router (im not talking streaming or stuff, jsut regular webpages) so he is limitimg me to 5 tabs at a time... i usually have about 50-75... does this affect him? if not, he says if i can print out proof that it doesnt effect him, i can have my tabs back! where can i find proof?

---

### Post by jbrown96 on 2009-06-10
You could show him the network traffic that your computer is generating. There is a system monitor in System--->admin that creates nice graphs for network use. You should be able to do something like the following. Open up all your tabs in Firefox and the system monitor, then close Firefox and choose to "save and exit". When you reopen firefox, it will load all your tabs, so the graph will spike really high. This shows what happens when a lot of web pages are loaded, but the graph should drop to zero as soon as all the pages are loaded. This proves that the only reason the network is being used is when the pages are actually requested, then the network activity drops off. 

Your dad's argument is persuasive, but not for the right reasons. Having lots of tabs open does not increase your network usage, but it may affect your network use. That is, you probably end up browsing more when there are more tabs open, but the tabs themselves do not cause network performance penalties for other users. An artifical limit on the number of tabs you are allowed to use will not affect the network performance of your father. 

Obviously this all goes out the window if you have internet radio or something streaming in inactive tabs, but you seem to know this in your post. Just use the system monitor; it should definitively show that idle tabs aren't creating the slow-down. Something else to consider is using something like Flashblock, No-script, or Ad-block Plus in Firefox, so that advertisements aren't using your bandwidth. I've found that they can really speed up browsing on slow connections.

---

### Post by asmoore82 on 2009-06-10
[SIZE="3"]**+1**[/SIZE] for SystemMonitor;
it also has a sister applet that you can add to the Gnome panel to see usage stats at a glance anytime.

---

### Post by SoftwareExplorer on 2009-06-10
Multiple words:Multiple Desktops, Multiple firefoxes

---

