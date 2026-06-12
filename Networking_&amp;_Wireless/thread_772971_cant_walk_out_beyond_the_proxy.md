---
title: "cant walk out beyond the proxy"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by hurinth on 2008-04-28
Hello, I am running version 7.10 32bit on this machine at work, where the network involves proxy settings to go out to the internet. Right now I am writing this from ubuntu, firefox, because I can set the Auto proxy to firefox itself, but if I try to search for updates, or even the the option to upgradee to 8.04, the update manager shows nothing. 

If I go to preferences>proxy, I see that the correct url is set for the automatic proxy configuration. I have used synaptic to download software and it installs it correctly.

Ne idea please?

---

### Post by jtrindle on 2008-04-28
There are at least three different places to set your proxy:

1) System->Preferences->Network Proxy Preferences 
2) System->Administration->Synaptic->Settings->Preferences->Network
3) Firefox->Edit->Preferences->Network->Settings

Also, make sure in your Synaptic->Settings->Repository you have the repositories turned on.  Then select "Reload" to see if the package list gets refreshed.

---

### Post by jtrindle on 2008-04-28
Also, check the Updates tab of the repository option to make sure you are getting more than just security updates.

---

### Post by hurinth on 2008-04-28
Thanks man, unfortunately everything is set from what you told me, i attached the images for you to look at them.

One question, I can download e.g, Kompozer packages for installation from Synaptic with the configuration shown in the screenshots, so it makes me think Synaptic is connected to the outsided, what about Update Manager? Ne way to set a proxy value directly for it? 

NOTE: I replaced the real ports and proxy value with fake characters (I need to cover my back)

---

### Post by hurinth on 2008-04-29
k now, updates suddenly began working after this thread, maybe I did something in the options I was playing with and that worked. 

However, I can't see how to upgrade to Hardy Heron via network, u know, in the Update manager. Is this only available for 64 bit environments? What could possible be wrong here?

---

### Post by hurinth on 2008-04-29
Another symptom is for example, when trying this command > sudo apt-get install alsa-base I get > Connecting to archive.ubuntu.com   0% The terminal sits there without progress.

Where can I set something for the system to know how to get out to the internet?


Thanks

---

