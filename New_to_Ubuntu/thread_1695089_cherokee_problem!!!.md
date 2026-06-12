---
title: "cherokee problem!!!"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by vivek.pandey on 2011-02-25
hi everyone 
  i am learning php so i need a server to test the codes and so i chose cherokee . well thought of some variation so didnt go installed it. installation was fine. but when i am trying to start the server by clicking on start the server tab i am getting an error...
here is it 
Something just happened while opening a plug-in file
The operating system reported '/usr/lib/cherokee/libplugin_rrd.so: cannot open shared object file: No such file or directory' while trying to load '/usr/lib/cherokee/libplugin_rrd.so'.

can anyone please tell what the problem and its solution might be

thanx in advance

---

### Post by vivek.pandey on 2011-02-25
k i decided to uninstall it. i went to synaptic and selected all packages marked and uninstalled it and selected the remove completely option to uninstall it completely but it seems some files are still there as when i type localhost in my web browser i get the testing page of cherokee server any suggestion please

---

### Post by vivek.pandey on 2011-02-25
anybody?

---

### Post by jnorthr on 2011-03-17
just had this happen to me. There is another module that needs to be loaded before cherokee will start successfully. You can confirm this by starting a terminal and using the command:
cherokee -t
which will test all the various bits before the server actually starts. This failure on the '...rrd' is because you have not installed the lib-cherokee-mod-rrd feature. you can use synaptic package manager to do this. In the search bar at the top of Synaptic, key in CHEROKEE and you will see which modules are installed on your system I'm looking for the items related to 1.2.1.1 maverick and found that several others were not installed, so i just marked all those for installation then did an APPLY. After it finished, i closed down my terminal just in case cherokee was hogging tcp port 9090. Also did this command before closing:
/etc/init.d/cherokee -status
to see the current status of the cherokee server. since i had an instance running, i did :
/etc/init.d/cherokee -stop
then closed the terminal. Reopened it and did:
/etc/init.d/cherokee start

now open a browser and put [http://localhost](http://localhost) in the address bar, and you should be there.

---

