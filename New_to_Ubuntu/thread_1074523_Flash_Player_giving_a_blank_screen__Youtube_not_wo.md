---
title: "Flash Player giving a blank screen / Youtube not working"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by Mega_Fauna on 2009-02-19
Hi,

I have installed "install_flash_player_10_linux.deb" which I downloaded from Adobe.com and flash isn't working properly.

Youtube just shows a black screen and various other (but not all) websites just show a white-space or whatever colour block they have chosen the page to be.

Prior to installing the adobe package I uninstalled all the flash files I could find through Synaptic as per some googled advice I'd previously found.

Can someone advise please?

---

### Post by superprash2003 on 2009-02-19
in firefox do you see something like "install missing plugins" at the top?

---

### Post by JK3mp on 2009-02-19
Did you download flash ff plugin

---

### Post by ubu_dynamite on 2009-02-19
Do you have both adobe flashplayer and flashplugin-nonfree instalt?

remove all flash
```
sudo aptitude purge mozilla-plugin-gnash
sudo aptitude purge adobe-flashplugin
sudo aptitude purge flashplugin-nonfree
```
and just install flashplugin-nonfree
```
sudo aptitude install flashplugin-nonfree
```
or if you realy want flash 10 just install it from the site but don,t install them both it will not work

---

### Post by Mega_Fauna on 2009-02-19
> **superprash2003 said:**
> in firefox do you see something like "install missing plugins" at the top?

Hi,

Thanks for the reply. No, I don't see the FF "install missing plugins" message. But I'm glad you asked, it's the sort of beginner embarrassment which occasionally occurs.

---

### Post by Mega_Fauna on 2009-02-19
> **JK3mp said:**
> Did you download flash ff plugin

Hi, 

Thanks for your response. 

The FF plugin page for flash takes me to the adobe site and to exactly the file I had installed from them.

---

### Post by Mega_Fauna on 2009-02-19
> **ubu_dynamite said:**
> Do you have both adobe flashplayer and flashplugin-nonfree instalt?

remove all flash
```
sudo aptitude purge mozilla-plugin-gnash
sudo aptitude purge adobe-flashplugin
sudo aptitude purge flashplugin-nonfree
```
and just install flashplugin-nonfree
```
sudo aptitude install flashplugin-nonfree
```
or if you realy want flash 10 just install it from the site but don,t install them both it will not work

Hi, thanks for your response.

I followed you instructions exactly, however the problem persists. 

Interestingly **about:plugins** doesn't list flash as a plugin, before or after your install instructions.

---

### Post by ubu_dynamite on 2009-02-19
I,m running hardy and Intrepid ad the moment so don,t have a machine to test it out.

I think you could better install one of those flashplugin-nonfree is working for me in both of them.

Ubuntu 7.10 Gutsy Gibbon End of life date is April 2009.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Mega_Fauna on 2009-02-19
Google is giving me other people with the same problem, but no working solution for me yet. See [this link]("http://www.youtube.com/watch?v=Oi1BcouEmio") for an example and the extent of the problem:

---

### Post by ubu_dynamite on 2009-02-20
I just found a pc with gutsy in a youth center i instalt it some time ago flash is working here.
the only flash package instalt on this pc is flashplugin-nonfree.

Try to remove al flash related packages and only install flashplugin-nonfree

backports is enabled on this pc no 3rd party sources added.

From add/remove aplications all gstreamer packages and Ubuntu restricted extras are also instalt on this pc.

---

### Post by Mega_Fauna on 2009-02-20
> **ubu_dynamite said:**
> I just found a pc with gutsy in a youth center i instalt it some time ago flash is working here.
the only flash package instalt on this pc is flashplugin-nonfree.

Try to remove al flash related packages and only install flashplugin-nonfree

backports is enabled on this pc no 3rd party sources added.

From add/remove aplications all gstreamer packages and Ubuntu restricted extras are also instalt on this pc.


Hi thanks for your post and all the effort.

I have done all the stuff you requested in your post. I have uninstallt all the flash files and reinstalt the flashplugin-nonfree alone. All the pertinent gstreamer files are in place (including all the good, the bad, and the ugly sets), and ubuntu-restricted-extras has been installt as well. I've even turnt the box off and on again.

So flash still doesn't work and right-clicking on the black video box on youtube tells me "Video not loaded" and "About flash" or something like that. Thanks for your suggestions.

---

### Post by pgdave on 2009-02-20
I have the same problem as the OP. My system was OK until recently (I think an upgrade of Firefox did the damage). Firefox started running flash, eg youtube videos intermittently. Somethimes they worked, sometimes they stopped after a few seconds, etc. Sometimes pressing 'reload' got them to work. 

I followed the instructions listed above. I noted that 'swfdec' was running the flash, so I used synaptic to remove swfdec. Now Firefox tells me that either I have not enabed javascript, or I have  an old version of flash. If I follow the URL, to download Flash, it then tells me that adobe-flashplugin is already installed.  I even removed FF, and re-installed, to nil effect.

Opera, on the other hand works perfectly, whatever I do to flash plugin(s). If I liked Opera, I'd abandon FF, but I don't.

EDIT: At one point, FF kept asking me to install plugins, and it gave me option of Flash, swfdec or gnash. The entry for flash said it had no database info, and selecting it told me it was already installed.  Aaargh!

---

### Post by gandaran on 2009-02-20
> So flash still doesn't work and right-clicking on the black video box on youtube tells me "Video not loaded" and "About flash" or something like that. Thanks for your suggestions.
__________________
you have a black flash video window? then you must have flashblock addon installed? disable it or remove it completely!

---

### Post by Mega_Fauna on 2009-02-20
> **gandaran said:**
> you have a black flash video window? then you must have flashblock addon installed? disable it or remove it completely!

Thank-you! That was it!

How on earth did I miss that for so long? And why didn't Flashblock show a button on the unflashed area as it usually did? IDK.

Anyways, thank-you once again.

[SOLVED]

---

### Post by mossi_92 on 2009-06-14
Does anyone know what this is?

---

### Post by SubCool on 2010-10-07
> **gandaran said:**
> you have a black flash video window? then you must have flashblock addon installed? disable it or remove it completely!

Not to revive an old thread like all hate,
but i have followed all the directions here, and for some reason my flash is doing the same, FF or Chrome.
I have disabled, and removed my add-ons. 

after i find how to run FF in safemode, if it works there, ill edit this. otherwise- help?

---

### Post by Lupi on 2010-10-09
I'm using Karmic 64-bit and use mainly Chrome. However, for some reason, the flash video pages go blank after a while. To add more weirdness, sometimes it takes a few seconds, other times it takes minutes. Any idea?

---

### Post by aala on 2010-10-09
just do this my friend in terminal or hotkeys alt+F2
and then:...
```

sudo apt-get install ubuntu-restricted-extras
```
```

sudo apt-get install kubuntu-restricted-extras
```
```

sudo apt-get install xubuntu-restricted-extras
```

according to whatever it is that you have.

Good luck!

---

### Post by aala on 2010-10-09
might want to install these too!!!
gecko-mediaplayer is the best plugin to play media for firefox, it works better than totem-mozilla (at least for me does!)
```
sudo apt-get install gnome-mplayer gecko-mediaplayer
```

and if you like chromium-browser (google-chrome)
if you want the full support for media, you have to install the extra and nonfree packages too, otherwise just install the browser alone!
```
sudo apt-get install chromium-browser chromium-codecs-ffmpeg-extra chromium-codecs-ffmpeg-nonfree
```

---

### Post by specialk1st on 2011-05-19
> **aala said:**
> just do this my friend in terminal or hotkeys alt+F2
and then:...
```

sudo apt-get install ubuntu-restricted-extras
```
```

sudo apt-get install kubuntu-restricted-extras
```
```

sudo apt-get install xubuntu-restricted-extras
```

according to whatever it is that you have.

Good luck!
just wanted to say that i was having the problem of the videos loading as a black screen in google chrome on ubuntu 11.04 natty and this solution worked perfectly for me.

thanks!

---

