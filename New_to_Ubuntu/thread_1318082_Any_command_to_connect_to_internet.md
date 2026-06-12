---
title: "Any command to connect to internet ?"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by praveesh on 2009-11-07
I used to connect to internet with the gprs of my nokia mobile phone with the help of network manager applet(nm-applet) in Gnome. The network manager plasmoid in kde cannot connect to internet using gprs(may be a bug). Just for connecting to internet, I need to switch to Gnome. Is there any command to use the Gnome network manager(or the network manager applet) to connect to internet so that I can use it in Kde?

Thanks

---

### Post by praveesh on 2009-11-07
Is there any other ways of solving the problem ? Any command line program other than Gnome network manager ?

---

### Post by praveesh on 2009-11-08
I found out a solution myself. Close the process knetworkmanager and start the process nm-applet . 

Code: 
killall knetworkmanager ;nm-applet 

nm-applet will appear in kde . Use it .

---

