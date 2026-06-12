---
title: "What java packages for yahoo games?"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by gordon33 on 2009-07-02
Hello

What Packages need to be in stalled from the Synaptic Package Manager in order to get yahoo games to play?  

The labtop has Ubuntu 9.04 instaled.

Gordon Webb

---

### Post by Michael.Godawski on 2009-07-02
Usually it suffices to install these
```

sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by sdlynx on 2009-07-02
hmmm there should be an option to install that will take you through the installation of the java runtime environment to play games written in java.  However I believe yahoo games are written in flash.  Again for flash it should be the same situation to install a missing plugin (look for a notification right below the address bar on the page with flash on it).

If that doesn't work open a terminal and type ```
sudo apt-get install flashplugin-installer
```

---

### Post by gordon33 on 2009-07-02
Hello sdlynx, and Michael.Godawski

In the past i have not had any luck with getting the needed java with sudo apt-get install.  I had much better luck with Synaptic Package Manager.  I just can not remember the packages i installed.

Gordon33

---

### Post by gordon33 on 2009-07-02
Hello

What other packages beside java would need to be installed?

Gordon33

---

### Post by gordon33 on 2009-07-02
Hello

From the Synaptic Package Manager I clicked on the java packages Michael.Godawski listed in his command sudo apt-get install.  I also  installed flashplugin-installer listed in sdlynx sudo apt-get install command.  

Gordon33

---

