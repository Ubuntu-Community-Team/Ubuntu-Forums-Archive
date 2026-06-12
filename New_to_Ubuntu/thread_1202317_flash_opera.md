---
title: "flash opera"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by Ajat on 2009-07-02
I installed iVersion: 9.64 Build:  2480  on my kubuntu 9.04  System i686.

then i install adobe flash to play youtube video.. video plays well but it has no sound.

I have seen some posts in this forum, but i think i can´t understand.

please help

---

### Post by mad_squirrel on 2009-07-02
Hi.
That sounds a bit weird. I'll suggest you a bit windowish way: try to reinstall flash player package(s). If you have Firefox installed, first remove it, reinstall flash player and install FF again.
That worked for me(although the problem was a bit different: video was not played at all).

---

### Post by Sef on 2009-07-02
How did you install Flash?

---

### Post by mad_squirrel on 2009-07-02
via synaptic.
the package is called flashplugin-installer
you may also install flashplugin-nonfree

---

### Post by .nedberg on 2009-07-02
Make sure flash works with sound in Firefox and Konqueror. Make sure flash is not muted and watch the same movie in all browsers.

I have no problem with flash in Opera 9.64 on Kubuntu 9.04. It just eats a lot of CPU, but that is more a flash problem than Opera.

You could also try the newer Opera 10. I am using it right now, and it works just fine! Go to [http://my.opera.com/desktopteam](http://my.opera.com/desktopteam) and dl a Opera for qt4. I use the tar.gz packages so I don't have to remove my 9.64 version. I just run it from the terminal.

---

### Post by Ajat on 2009-07-02
Hi. thanks for the replies.

I opened youtube and the videos didnt show, the site told me to download the latest flash player on [http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/)

I went to the site and  downloaded *.deb file.. and then i installed it. 

now the video can show but with no sound. I don´t have firefox here, my kubuntu is still fresh.

---

### Post by .nedberg on 2009-07-02
Do you have sound in other applications? Try to play some music.

And try flash with Konqueror also!

---

### Post by Ajat on 2009-07-02
i can hear the sound played at start up and can play mp3 files..

i also cannot hear the sound when openning from the konqueror.

---

### Post by .nedberg on 2009-07-02
OK, so we know it is not Opera!

I recommend you remove the flash you installed and do it the "Ubuntu"-way.

I would install kubuntu-restricted-extras...

```

sudo apt-get install kubuntu-restricted-extras

```

It will install some more packages also

---

### Post by .nedberg on 2009-07-02
Also, in Opera go to Tools->Preferences, Advanced tab->Content. Press "Plug-in Options" and click "Find new..." after reinstalling flash.

---

### Post by Ajat on 2009-07-02
Hi. how do i uninstall the plugin?

i try your code but getting this

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package kubuntu-restricted-extras is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kubuntu-restricted-extras has no installation candidate

```

any other suggestion?

---

### Post by .nedberg on 2009-07-02
to remove try
```

sudo dpkg -r <name of the flash-package you installed>

```

the error might mean you don't have the restricted/multiverse repositories enabled.
Open Adept, sources tab and click "Edit sources". On the "Kubuntu Software" tab everything should be selected. If it already is selected, click Close, the "Fetch current package list" and do a search for kubuntu-restricted-extras and install it.

---

### Post by Ajat on 2009-07-02
> **.nedberg said:**
> to remove try
```

sudo dpkg -r <name of the flash-package you installed>

```

the error might mean you don't have the restricted/multiverse repositories enabled.
Open Adept, sources tab and click "Edit sources". On the "Kubuntu Software" tab everything should be selected. If it already is selected, click Close, the "Fetch current package list" and do a search for kubuntu-restricted-extras and install it.
Where can i find this "Adept"?

I have no idea about the package name.. where can i find/know it? I got the package from 
[http://get.adobe.com/flashplayer/?promoid=DXLUJ](http://get.adobe.com/flashplayer/?promoid=DXLUJ) 
where i choosed ".deb for Ubuntu 8.04+" version. then i executed the deb file.

if i go to Preferences-> Advanced -> Plug-in Option, it says

**Name:** Shockwave Flash **Description**: Shockwave Flash 10.0 r22

i have tried: 
```
sudo dpkg -r Shockwave Flash 
```

and

```
sudo dpkg -r Shockwave Flash 10.0 r22 
``` 

with " "  or ' ' , none of those worked. I also go to usr/lib/opera/plugins where i can find libesd.so.1 and try

```
sudo dpkg -r libeso.1 
``` 

I also tried:

```
sudo dpkg -r install_flash_player_10_linux.deb 
```

where install_flash_player_10_linux.deb is the file i got from the website.

Not working.. T_T

thanks for your replies.

---

### Post by .nedberg on 2009-07-02
Press Alt+F2, type 'kdesudo adept' and hit enter

Do a search for flash. One package will be installed, that will be the one you downloaded. Remove it and follow above instructions.

---

### Post by Ajat on 2009-07-02
i did 'kdsudo adept' but then i get "command not fount!"

i'm using fresh install of kubuntu 9.04 here.. should this "adept" was here from the beginning? or do we need to install it?

thanks.

edit: I think adept is no longer available in kubuntu 9.04, it is replaced by KPackagekit

---

### Post by .nedberg on 2009-07-02
Sorry for not getting back to you earlier. I have been out swimming!

Yeah, Adept might be replaced by KPackageKit. Did you try my suggestions? Did it work?

I am away from my Kubuntu system for today, but I will try to help if I can!

---

### Post by Ajat on 2009-07-02
I have installed kubuntu-restricted-extras and uninstall the adobe flash 10.

now i don't have any flash player. (i have refreshed the plugins on opera by clicking find new) 

the browser tells me to get the latest flash player.

what should i do now?

thanks

---

### Post by .nedberg on 2009-07-02
> **Ajat said:**
> I have installed kubuntu-restricted-extras and uninstall the adobe flash 10.


If you did it in that order then you would end up with no flash player.

Try this:
```

sudo apt-get install flashplugin-nonfree

```

If it works and you regain the ability to play flash videos without sound, then install Firefox
```

sudo apt-get install firefox

```

and see if it works. 


Going to bed now, be back tomorrow.

---

### Post by Ajat on 2009-07-04
it still not working..

i ahve the flashplugin-nonfree and firefox here .. but still can't here the sound..

anyway thanks for replies, indeed i learn much ;).

---

### Post by .nedberg on 2009-07-05
I am not sure this will help, but there seems to be a extra package for flash and other soundsystems. You could give it a try:
```

sudo apt-get install flashplugin-nonfree-extrasound

```

---

### Post by falen_pl on 2009-07-05
> **.nedberg said:**
> 

You could also try the newer Opera 10. I am using it right now, and it works just fine! Go to [http://my.opera.com/desktopteam](http://my.opera.com/desktopteam) and dl a Opera for qt4. I use the tar.gz packages so I don't have to remove my 9.64 version. I just run it from the terminal.

Hey, can you explain how to run Opera 10? I DL'ed the file, installed it thru terminal to default directory (/home/lib/opera/10/) and tried running it by double clicking on 'opera' file. It seemed to run OK, until I found out there's no address bar and clicking anywhere on the screen does nothing. My ubuntu installation is fresh so I'm probably missing some stuff for 10 to run properly. Can you point me in the right direction? 

I swear to God, Linux version of Opera will be the end of me. I can't get Flash and Java to work and the funny thing is, those two work flawlessy in Firefox. However, I have no problem giving up on a lot of Windows applications such as iTunes, but I can't imaging walking out on Opera. I'm hoping ver.10 will fix things. 

Thanks in advance!

---

### Post by falen_pl on 2009-07-05
Well, well...I'm not quite sure HOW but the whole mess fixed itself. I got rid of 9.64 and installed 9.62 in hope this will help with flash/java but with no result. I restarted the system, launched Opera and...10 booted up! Maybe the problem was with not uninstalling 9.64 before trying 10? 9.62 is still in /usr/lib and 10 in /home/lib/ I'm so confused about the whole thing but the most important thing is I finally got flash/java working in Opera. 10 works beautifuly! Not only is it eye candy but they improved performance. My advice to anyone having problems with running flash in Opera. Give the latest version a try, and don't be discouraged by the fact it is still beta. It works.

---

### Post by .nedberg on 2009-07-06
> **falen_pl said:**
> and don't be discouraged by the fact it is still beta. It works.

If you go to the desktopteam then you get a weekly snapshot, it is not even considered alfa...

Anyway, I am using the latest build right now! Here is how I do it:

[LIST=1]
[*]DL the latest snapshot, I always get the tar.gz-version
[*]Unpack it
[*]cd to the folder where you unpacked it
[*]run in with ./opera
[/LIST]

You can get a version for 32bit here: [http://snapshot.opera.com/unix/snapshot-4464/intel-linux/](http://snapshot.opera.com/unix/snapshot-4464/intel-linux/)

If you don't want to bother with dependencies get one of the 'bundled' versions. Right now there is no qt3 builds, due to an error.

"Installing" Opera this way does not mess with any other version on your machine, and it is easy to remove (just delete the folder). It does not touch your original .opera folder with setting either.

---

### Post by falen_pl on 2009-07-14
I used your method and it worked. A few days ago I found another way to install the latest snapshot. 

Adding this line to sources.list

*deb [http://deb.opera.com/opera-snapshot/](http://deb.opera.com/opera-snapshot/) sid non-free*

Add the key

*sudo wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -*

and then, after updating:

*sudo apt-get install opera*

That's it. Opera will be installed in /home/.opera 


One question, though. What plugin did you use to view WMP/MOV I can't seem to make'em play. I'd really appreciate your help.

---

### Post by .nedberg on 2009-07-14
> **falen_pl said:**
> 
One question, though. What plugin did you use to view WMP/MOV I can't seem to make'em play. I'd really appreciate your help.

I use mozilla-mplayer.

---

### Post by falen_pl on 2009-07-14
Can you tell me how you installed it? I'm having problems with properly displaying WMP and MOV's. I tried installing it thru synaptic and indeed, it was in mozilla/plugins folder. I made Opera use it but it still couldn't view WMP/MOVs. I also moved them to Opera's plugin folder, but still no luck. I heard the plugin needs to be installed thru Gecko sdk but I've no idea how to go about it. 


Basically what I need to know is:

1) how you installed the plugin
2) what you assigned to use that plugin in Opera/tools/prefs/advanced/downloads

Thanks

---

### Post by .nedberg on 2009-07-14
Pretty sure I got it from [medibuntu]("https://help.ubuntu.com/community/Medibuntu")

```

sudo apt-get install mozilla-mplayer

```
or use adept/synaptic

All files with .mov extension is set to be opened with the plug in.

But when I go to [http://trailers.apple.com](http://trailers.apple.com) I find none that work at the moment... It has been a while since I used it... It works on other pages though...

Any page/file you want me to try?

---

### Post by falen_pl on 2009-07-14
I managed to view this page with gecko player 

[http://teledyski.onet.pl/10173,5234979,teledyski.html](http://teledyski.onet.pl/10173,5234979,teledyski.html)

BUT

when I try to view this one:

[http://wiadomosci.onet.pl/5276141,1,1,1,relacjetv.html](http://wiadomosci.onet.pl/5276141,1,1,1,relacjetv.html)

Opera moans about no having java scripts enabled (which is false). It's weirds because I though those two are handled by the same plugin.

When you installed mozilla-mplayer, which entries did you associated with that plugin in tools/pref/advanced/downloads?

---

### Post by .nedberg on 2009-07-14
None of those worked for me. mplayer-plugin appeared, but did not play anything.

I did not manually assign mplayer to anything, that was done by opera. Quite a lot is set to be opened with the plug in, to much to post here...

---

### Post by falen_pl on 2009-07-14
All right, I actually managed to fix this mess. I can now view WMP and QT (including apple.com/trailers). 

I followed this guide:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Got rid of every plugin, installed gecko player, emptied Opera's plugin folder, restared the system. Both player work no problem. 

Before installing gecko, I tried the same thing with mplayer and, to my amazment, mozilla couldn't handle neither WMP nor QT. So it wasn't Opera's fault after all - the mplayer plugin is messed up. 

So if you can't view apple.com/trailers you might give gecko a shot. 

I also learned that by going to about:plugins in mozilla, I can view a list of every file type, its extension and plugin assigned to it. A good reference list if I needed to change some associations in Opera. 

Anyway, thanks for help. Take care, buddy. :guitar:

---

