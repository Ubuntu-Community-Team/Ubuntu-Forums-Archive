---
title: "Ubuntu will not allow me to download firefox add-ons"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by deancasino on 2009-12-12
It's the weirdest thing, I cannot get Ubuntu to download add-ons from [https://addons.mozilla.org/en-US/firefox/](https://addons.mozilla.org/en-US/firefox/) at all. I have:


[LIST=1]
[*]Deleted the firefox profile (and created a fresh one)
[*]Reinstalled firefox (After completely deleting all firefox related folders in home)
[*]Tried to download the add-ons manually with;
[/LIST]

[LIST]
[*]Google Chrome
[*]Chromium
[*]Epiphany
[*]Gwget Download Manager
[*]Firefox
[/LIST]
I've hit a brick wall now, I'm totally out of options.

Anyone help?

---

### Post by ~sHyLoCk~ on 2009-12-12
Did you try searching within the firefox addon and adding them? Like: Tools->Addons->Get-addons

What does it say when you try to install?

---

### Post by deancasino on 2009-12-12
It just displays as "connecting..." for ages

---

### Post by deancasino on 2009-12-12
If it helps, when I do try to download any add-on, if I do get a notification (I don't usually) it reads:

Firefox could not download the search plugin from:
[https://addons.mozilla.org/en-US/firefox/downloads/latest/10423/addon-10423-latest.xml](https://addons.mozilla.org/en-US/firefox/downloads/latest/10423/addon-10423-latest.xml)

---

### Post by ~sHyLoCk~ on 2009-12-12
> **deancasino said:**
> It just displays as "connecting..." for ages

That's weird. Usually it takes a few seconds here. Hmm, I don't know what's up but if you want try this:
```

sudo apt-get remove firefox --purge
sudo apt-get update
sudo apt-get install firefox

mv ~/.mozilla mozbak
```

Now open firefox and retry fresh.

Hopefully it will work.

---

### Post by deancasino on 2009-12-13
Thanks you for your help by the way, seems like your solution half worked, I get an error now;

Firefox could not install the file at 

[https://addons.mozilla.org/en-US/firefox/downloads/latest/539/addon-539-latest.xpi?collection_id=da0ecd99-2289-7ab0-7d57-e7c489c845c3&src=homepagepromo](https://addons.mozilla.org/en-US/firefox/downloads/latest/539/addon-539-latest.xpi?collection_id=da0ecd99-2289-7ab0-7d57-e7c489c845c3&src=homepagepromo)

because: Download error
-228

---

### Post by ~sHyLoCk~ on 2009-12-13
Damn. It installed for me. :\

Ok do this:

1. Go [here]("https://addons.mozilla.org/en-US/firefox/addon/539")
2. Downlod the .xpi file by right clicking on it and "Save Link as.."
3. Next, go to the Firefox drop down menus at the top of the browser. Select File > Open File then select the addon.xpi file and click on Open. The Software Installation window will appear, click install, restart Firefox.

---

### Post by superdan006 on 2009-12-13
Is you cache disabled by chance?
[http://kb.mozillazine.org/Unable_to_install_themes_or_extensions_-_Firefox#Download_Error_-228](http://kb.mozillazine.org/Unable_to_install_themes_or_extensions_-_Firefox#Download_Error_-228)

Go to Edit -> Preferences -> Advanced -> Network
I have my cache at 50 mb, what is yours at?

---

### Post by deancasino on 2009-12-13
I've up-ed it to 60MB, no luck

---

### Post by superdan006 on 2009-12-15
Sorry that couldn't work. I'll keep searching.

---

### Post by nightmicu on 2009-12-16
I am having this exact same problem, glad it's not just me! I am running Firefox 3.5.5 on Ubuntu 9.10 64 bit. 

I've had a lot of other issues, namely Flash, that seem to be due to the fact that I am running 64 bit... could this also be a factor with the Add-On issues?

---

### Post by 1915flyer on 2009-12-17
Same problem, both with an upgrade 9.04 to 9.10 and a fresh install of 9.10 on the same computer. Firefox 3.5.5. Takes forever to connect after selecting the addon, then another long time before the following message comes up.

"Firefox could not install the file at 
[https://addons.mozilla.org/downloads/file/71956/fireftp-1.0.7-fx.xpi?src=api](https://addons.mozilla.org/downloads/file/71956/fireftp-1.0.7-fx.xpi?src=api)
because: Download error
-228"

This was for FireFTP, but I have had problems with a number of other addons including adblock and noscript.

They load under WindowsXP Pro with no problem.

---

### Post by 1915flyer on 2009-12-19
Bump

My desktop running ubuntu 9.10 and Firefox 3.5.5 has no problem with the addons. This computer, a Dell laptop and running the same, times out trying to connect and download the addons.

Could it be something about the permissions settings of the files in the .mozilla directory?

---

### Post by ankspo71 on 2009-12-19
Hi
Can either of you install addons from other sites? Try this, just to see if they install or not...



Google Toolbar.
[http://www.google.com/toolbar/ff/index.html](http://www.google.com/toolbar/ff/index.html)

If this works, then there might be something on your systems that are blocking installations/downloads from the Firefox addons site only.

Also, be sure addons.mozilla.org is set to allow installing addons in Edit > Preferences > Security > "warn me when sites try to install addons" > Exceptions.    < -- Nevermind, I thought there was a block option too.

---

### Post by ankspo71 on 2009-12-19
This link covers several problems including the the -228 error.
[http://kb.mozillazine.org/Unable_to_install_themes_or_extensions_-_Firefox](http://kb.mozillazine.org/Unable_to_install_themes_or_extensions_-_Firefox)

Another..
[http://support.mozilla.com/en-US/kb/Unable+to+install+add-ons](http://support.mozilla.com/en-US/kb/Unable+to+install+add-ons)

---

### Post by 1915flyer on 2009-12-19
I installed the Yahoo toolbar OK but that was a big mistake. Now nothing works or shows in the Tools/Addons menu except the icons at the top. Search for addons does nothing, just hangs, and there's no provision to uninstall Yahoo. None of the addons originally installed with Firefox show.

Looks like a reinstall of Firefox is in my future.

[time passes]

Whew, managed to hunt down the Yahoo toolbar in .mozilla and kill it! My originally installed addons are back.

I have managed to install one addon called METARWatch several days ago  even though it said it was "experimental". Not much else seems to work though.

I've tried to mozilla.org suggestions. Cache is 50mb. How do you change the firefox server - or is it the ubuntu server that I have to change?

---

### Post by ankspo71 on 2009-12-19
> **1915flyer said:**
> I installed the Yahoo toolbar OK but that was a big mistake. Now nothing works or shows in the Tools/Addons menu except the icons at the top. Search for addons does nothing, just hangs, and there's no provision to uninstall Yahoo. None of the addons originally installed with Firefox show.

Looks like a reinstall of Firefox is in my future.

[time passes]

Whew, managed to hunt down the Yahoo toolbar in .mozilla and kill it! My originally installed addons are back.

I have managed to install one addon called METARWatch several days ago  even though it said it was "experimental". Not much else seems to work though.

I've tried to mozilla.org suggestions. Cache is 50mb. How do you change the firefox server - or is it the ubuntu server that I have to change?

Hi,
After reading what you posted, I tried the yahoo toolbar myself and it did the same to me. I got rid of it by deleting /home/james/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384} then restarted firefox twice. It's gone now. Sorry about that.

I'm not sure what to do about changing servers/mirrors... changing your ubuntu mirrors wouldn't solve the problem, but it might increase your download speeds for packages.

There are some addons available in synaptic package manager, but it is only a small selection. adblock-plus is in there. Try searching for some of your needed addons in there. 

Here are some mozilla mirrors. The primary mirrors linked here has a sub directory for addons. [http://www.mozilla.org/community/mirrors.html](http://www.mozilla.org/community/mirrors.html) I don't see a way to search the mirrors though.

Although, you can also get the filenames of the addons by right clicking on them and select save link as, copy the filename and search google for a download link. 

Hope this helps.

---

### Post by ankspo71 on 2009-12-19
Hi,
Go to google.com and search for ```
fireftp xpi 2009 intitle:index.of

```I knew there was something I forgot to say.

This could be an ubuntu problem (bug), so anyone who has these problems should see about reporting them. [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Edited for updating the search terms

---

### Post by joes7 on 2009-12-19
You can try by re-installing, if it is a FF problem. Alternately you can log in as the "root" user. That gives you 100% access.

---

### Post by okenobu on 2009-12-21
I've been struggling with this problem as well, and finally found a solution. _Please note I don't really know how the following hack affects the rest of applications_, but at least this way i can download adblock :P

Original post at [http://www.pablomarcos.es/solucion-actualizacion-complementos-firefox-error-228-en-ubuntu-9-10-karmic/]("http://www.pablomarcos.es/solucion-actualizacion-complementos-firefox-error-228-en-ubuntu-9-10-karmic/"). It's in spanish, so you can try google translation or similar.

_Quick how-to_:

1. Edit **/etc/dhcp3/dhclient.conf**

Change line starting with 'prepend domain-name-servers' (might be commented) to:

```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```

2. Edit **/etc/nsswitch.conf**

Replace the following line:

```
files mdns4_minimal [NOTFOUND=return] dns mdns4

```
with:

```
hosts: files dns
```

3. Reboot

Voila!

Hope it helps

---

