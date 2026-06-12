---
title: "Installing Polipo (or, at least, trying...)"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2011-09-08
Ok, so, I'm trying to install Polipo in my laptop, on a fresh Lubuntu install.

I'm following the instructions in this page:

[https://help.ubuntu.com/community/Tor#Install_Polipo_.28an_HTTP_proxy.29](https://help.ubuntu.com/community/Tor#Install_Polipo_.28an_HTTP_proxy.29)

Of course, as usual, nothing works as expected.

After finding (thanks to several members here) a way to add the universal repositories, I could finally use

> sudo apt-get install polipo

and everything seemed to be perfect.

Then, when I tried 

>  sudo mv -i /etc/polipo/config /etc/polipo/config.orig
I got a message: 

> 

mv: cannot stat '/etc/polipo/config': No such file or directory

The thing is, I've been looking for the Polipo files everywhere, and I can't find them. Help, please??

Thanks in advance. :)

---

### Post by Inodoro Pereyra on 2011-09-08
Ok, finally, after going up a couple of times, I managed to find the /etc/polipo folder, in the root directory.

Now, in the instructions, it says to "download" Torproject's Polipo configuration for Tor, and put it in place of the current config file, but, when I click on the link, it just shows me a listing, and doesn't give me the option to download anything.

Should I copy/paste the listing on leafpad, and then move the file to the polipo folder?

---

### Post by haqking on 2011-09-08
> **Inodoro Pereyra said:**
> Ok, finally, after going up a couple of times, I managed to find the /etc/polipo folder, in the root directory.

Now, in the instructions, it says to "download" Torproject's Polipo configuration for Tor, and put it in place of the current config file, but, when I click on the link, it just shows me a listing, and doesn't give me the option to download anything.

Should I copy/paste the listing on leafpad, and then move the file to the polipo folder?


just save the file as it is shown and then place that in the config directory, keeping a backup of the original, from your browser when it is displayed choose file save and it should append .conf to file name

---

### Post by Inodoro Pereyra on 2011-09-08
> **haqking said:**
> just save the file as it is shown and then place that in the config directory, keeping a backup of the original, from your browser when it is displayed choose file save and it should append .conf to file name

It won't let me. :(
When I try to save, I get a message saying "The folder contents could not be displayed."

---

### Post by haqking on 2011-09-08
> **Inodoro Pereyra said:**
> It won't let me. :(
When I try to save, I get a message saying "The folder contents could not be displayed."


save it to your desktop or whereever then use the mv command as outlined previously adjusting for location

---

### Post by Inodoro Pereyra on 2011-09-08
I'm confused. (sorry, I've been up all night).
Do you mean save the page from the browser, or copy/paste into leafpad and save?

If I try to save from the browser, I keep on getting the same message, regardless of destination. I tried copy/pasting on leafpad and saving, and everything seems ok...

Sorry if I seem stupid. I know I can make a real mess, if I make a mistake working on root, and I don't want to.](*,)

---

### Post by Inodoro Pereyra on 2011-09-08
Ok, considering the lack of a reply (and the fact that I'm tired), I decided to take the risk, copy/paste the config file on leafpad, and move it to the polipo directory.

Now, I have 2 problems:

1. How do I know if Polipo is running?

2. in the Polipo page I linked above, it says to "Check that the Tor service is running on port 9050" by typing

> ss -aln | grep 9050

I did, and nothing happened. So I configured Tor Browser, according to these instructions:

[https://www.torproject.org/docs/tor-doc-web.html.en](https://www.torproject.org/docs/tor-doc-web.html.en)

But, when I restart the Tor Browser, all the settings change to what they were before. How do I configure the Tor browser permanently, to work with Polipo?

---

### Post by Inodoro Pereyra on 2011-09-09
Nobody? :(

---

### Post by bodhi.zazen on 2011-09-09
See if this helps:

[http://bodhizazen.net/Tutorials/TOR](http://bodhizazen.net/Tutorials/TOR)

---

### Post by Inodoro Pereyra on 2011-09-09
Thank you Bodhi-Zazen. I'm in the process of reading it right now.
Will report back. :)

---

### Post by Inodoro Pereyra on 2011-09-09
Ok, I'm at a loss.

I followed the instructions to the letter. Made a new config file for Polipo exactly like the one shown (without the last 3 comment lines), and restarted polipo. Everything was running perfectly.
Then, I configured the browser as recommended: Proxy 127.0.0.1, Port 8123, and checked the "Use this proxy server for all protocols" box.

Then, I tried to set the system wide proxy. There's no "Network settings" (that I could find, at least) in Lubuntu. Being that I couldn't set the system wide proxy, I skipped the "configuring your browser to use system proxy" part.

Then, I tried configuring the Tor button, but, for some reason, the "Use Polipo" instruction is grayed out, and won't let me activate it.
What am I doing wrong?](*,)](*,)

---

### Post by bodhi.zazen on 2011-09-09
Restart polipo, tor, and firefox.

---

### Post by Inodoro Pereyra on 2011-09-09
Ok, just did. 
When I restarted firefox, it had lost the settings.
I tried the torbutton preferences before changing the settings, and the "Use Polipo" box was still grayed out. So I closed it, and edited the preferences on Firefox, and then went back to the Torbutton. Still the same. :(

---

### Post by Inodoro Pereyra on 2011-09-10
Anybody? :(

---

