---
title: "Thunderbird 3.1 is out as a tar... how do I install???"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by phubert28 on 2010-06-25
I've downloaded Tbird 3.1, but I don't see how to INSTALL it in 10.4.

Synaptic has something about adding a downloaded package, but it's looking for another format, apparently.

---

### Post by LowSky on 2010-06-25
I'll make it easier, download the .deb verison form here
[http://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/t/thunderbird-mozilla-build/thunderbird-mozilla-build_3.1-0ubuntu1_i386.deb/download](http://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/t/thunderbird-mozilla-build/thunderbird-mozilla-build_3.1-0ubuntu1_i386.deb/download)

this one is point and click to install

---

### Post by phubert28 on 2010-06-25
So why doesn't Mozilla do that??? (wry smile)

---

### Post by phubert28 on 2010-06-25
But I didn't mention that I have 64 bit  10.4

---

### Post by jre6 on 2010-06-25
I know I may be wrong (as these are for Firefox), but still...

[LIST]
[*]Download the Thunderbird tarball (the .tar.bz2 file) and extract in your home directory.
[*]Open a terminal window and type:
[/LIST]
```

~/thunderbird/thunderbird

```
[LIST]
[*]You may create the launcher and menu entries by giving the location as /home/username/thunderbird/thunderbird. For icons, see /home/username/thunderbird/icons/mozicon128.png.
[/LIST]

---

### Post by jre6 on 2010-06-25
I know I may be wrong (as these are for Firefox), but still...

[LIST]
[*]Download the Thunderbird tarball (the .tar.bz2 file) and extract in your home directory.
[*]Open a terminal window and type:
[/LIST]
```

~/thunderbird/thunderbird

```
[LIST]
[*]You may create the launcher and menu entries by giving the location as /home/username/thunderbird/thunderbird. For icons, see /home/username/thunderbird/icons/mozicon128.png.
[/LIST]

---

### Post by phubert28 on 2010-06-25
Linux continually disappoints when compared to Windows on issues like this.

I wonder if the DOWNLOAD is for 64 bit?

The i386 package fails.

---

### Post by manuelb on 2010-06-25
> **phubert28 said:**
> I wonder if the DOWNLOAD is for 64 bit?

AFAIK Mozilla still releases 32bit only builds.. and that's a shame.

---

### Post by phubert28 on 2010-06-25
So, at this point I'm wasting my time. And again the fault isn't with Linux, it's with the PROVIDERS.

I followed something on the web and ended up with a nightly build called (ominously?) "Shredder"

:lol:

Used to do FF nightly builds all the time on Windows - early days, 0.9 release and after.

...got beyond that, tho.

---

### Post by manuelb on 2010-06-25
You could look at the last post [here]("http://ubuntuforums.org/showthread.php?t=1457609")

You are going to compile your version from sources, don't know if you are proficient in the command line, but it seems that's the only way there is for now.

---

### Post by phubert28 on 2010-06-25
Well, that FIRST references adding a ppa to the repository sources ... and I think I already HAVE the one referenced, but it doesn't yet see the new tbird.

---

### Post by manuelb on 2010-06-25
Yes, i just checked it and that's the old 3.0.5, so i'm going to try compile my own .deb package.
If you have some time try stick here, i'm downloading the sources right now: i'll post updates while working on it.

---

### Post by phubert28 on 2010-06-25
Thanks for the reference info, manuelb. I don't think I'll try the compile tho. Done it for other things, but email is a tad too important for me to try a jerry-rigged approach.

---

### Post by manuelb on 2010-06-25
Ok, this is huge and i think i'll need a couple of minutes to compile everything and build a package..

---

### Post by phubert28 on 2010-06-25
:-)

---

### Post by manuelb on 2010-06-25
> **phubert28 said:**
> Thanks for the reference info, manuelb. I don't think I'll try the compile tho. Done it for other things, but email is a tad too important for me to try a jerry-rigged approach.

Don't worry, backup your .thunderbird|.mozilla-thunderbird or whatever your folder is called and you are ready to go and move your mail between installation: do a couple of tries, see how simple it is to transfer your whole settings just copy-pasting that folder ;)

---

### Post by phubert28 on 2010-06-25
I think you're going to be ready to give up on ME REALLY soon!
Heck, I don't even KNOW what directory Tbird was installed to!

But I can poke around.

I've probably screwed-up Synaptic as well... have some errors there after adding ppa's.

---

### Post by phubert28 on 2010-06-25
Weird. So, Linux doesn't do an "All Users" install? How inefficient!

Found the .thunderbird as well as a Thunderbird under root. ???

Wouldn't it just install to the same directory, keeping the mail and address book files???

And how DOES one backup?

:-) never did that under Windows (reckless guy)

I do see COPY (Nautilus is a little brain dead at times, no button for mkdir, among other things)

...do I have to take that back (File > Create Folder)

---

### Post by manuelb on 2010-06-25
Have you added the GPG keys for each PPA? That would cause *a lot* of verbosity during "apt-get update" or update-manager.

---

### Post by phubert28 on 2010-06-25
No. And, yes, that is exactly the sort of error I'm seeing. I didn't see any instructions for adding the keys... only the ppa's.

Created a dir "backup" and pasted .thunderbird into it.

Hard to get the "Windows way" out of my head after so many years on the platforms there.

---

### Post by manuelb on 2010-06-25
> **phubert28 said:**
> Found the .thunderbird as well as a Thunderbird under root. ???

The right folder to backup is the one Thunderbird itself is using: right-click on the account name, choose settings, then "server settings" from the left pane under the account name.
Look at the lower right under "local directory", that should look like "/home/xyz/.thunderbird" or something on these lines: check other accounts, if any, they should live there too.
Just backup this ".thunderbird" and you are pretty much done.

---

### Post by manuelb on 2010-06-25
> **phubert28 said:**
> No. And, yes, that is exactly the sort of error I'm seeing. I didn't see any instructions for adding the keys... only the ppa's.

With Lucid there is a faster way to add PPA *and* the GPG keys at once: just "sudo add-apt-repository <rep_name>" and you are done.

---

### Post by phubert28 on 2010-06-25
I will have to add this to my Tomboy notes! :-D I have lots already.

I'd already found the directory, thanks. And thanks for pointing me to something I'd already seen but forgotten (server settings, local dir)

NOW I have to figure out which  entries don't have their keys!
Remove and then add them again, I s'pose.

Or LIST them all, Revert and then Add.

---

### Post by manuelb on 2010-06-25
> **phubert28 said:**
> Remove and then add them again, I s'pose.

Yes, but can't remember how to list repos without keys ;-\
Anyway, it seems the source package mozilla distributes have some in compiling it, so just let me look at it, it MUST compile ;)

---

### Post by phubert28 on 2010-06-25
Too bad I learned all MY systems & programming on RCA (and other) mainframes... tho PC's didn't EXIST then and UNIX wasn't really well-known in places like the Calif. DMV in the 70's.

---

### Post by manuelb on 2010-06-25
> **phubert28 said:**
> Too bad I learned all MY systems & programming on RCA (and other) mainframes... tho PC's didn't EXIST then and UNIX wasn't really well-known in places like the Calif. DMV in the 70's.

How cool it was managing and programming mainframes? I imagine everyone looking at you as a master of some sort of obscure black art :twisted:

---

### Post by manuelb on 2010-06-25
Ok, going to have a cig then checking the package currently building.

---

### Post by phubert28 on 2010-06-25
This one was just posted at varlinux.org

[http://www.makeuseof.com/tag/nautilus-elementary-simplifies-file-browsing-linux/](http://www.makeuseof.com/tag/nautilus-elementary-simplifies-file-browsing-linux/)

sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa
sudo apt-get update
sudo apt-get upgrade

killall nautilus


I'll probably try it...

---

### Post by manuelb on 2010-06-25
Ok, the package is ready, now i need to upload it somewhere for you to download.
For your own and you all reference, keep in mind this package has been built configured straight from sources, with these settings:

```
./configure --enable-application=mail --enable-static --enable-calendar --enable-official-branding --disable-ogg --disable-wave
```

Then built with:
```

export CPLUS_INCLUDE_PATH=$CPLUS_INCLUDE_PATH:/home/manuel/downloads/comm-1.9.2/mozilla/content/media/
make -j8
(the source package didn't automatically include the "nsMediaDecoder.h" include files, so the "export" is just for that)

```

.deb package built with:
```

sudo fakeroot checkinstall -D --install=no --pkgname='thunderbird' --pkgversion='3.1.0'

```

```

Help->About: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.4) Gecko/20100625 Thunderbird/3.1

```

It should replace the previous package, 3.0.5, but for some reason the icon and the menu entry are lost: just pick an icon from your "/usr/local/lib/thunderbird-3.1/chrome/icons/default" and you should be done.
From now on, we should be able to "Check for updates" from the "Help" menu.

Please, if you have more information on how to maintain the icons, menu entries or something else, let me know, i'll try to keep an eye on this thread.

**Rapidshare.com**
```
http://rapidshare.com/files/402734363/thunderbird_3.1.0-1_amd64.deb.html
```

---

### Post by phubert28 on 2010-06-25
Fairly amazing, manuelb. Thanks much!

May not get back to this right away, tho... but I _will_ report back.

---

### Post by phubert28 on 2010-06-25
When I tried to run it, manuelb, I got the following:
[B]
[COLOR=Red]Error: Breaks existing package 'thunderbird-locale-en-gb' conflict: thunderbird (> 3.1~al)[/COLOR][/B]

So, NOW Synaptic sees the mozilla package, perhaps???

Is the 3.0.6 nightly build I picked-up seen as a 3.1????
I see no other.

Dunno how I managed to get an en-gb package, tho... since it should be en-us or somesuch.

---

### Post by manuelb on 2010-06-25
Let me know how it works for you: i think i should have specified something for the package information shown before installation but i'm too lazy to look up how to do that \\:D/

---

### Post by phubert28 on 2010-06-25
Well, you see it didn't work... conflict? THAT one has me puzzled.

---

### Post by manuelb on 2010-06-25
Any error information? Could you install the package successfully?

---

### Post by phubert28 on 2010-06-25
The message I posted below:

 				 				**Re: Thunderbird 3.1 is out as a tar... how do I install???** 			
 			 			 		   		 		 		When I tried to  run it, manuelb, I got the following:
[B]
[COLOR=Red]Error: Breaks existing package  'thunderbird-locale-en-gb' conflict: thunderbird (> 3.1~al)[/COLOR][/B]

So, NOW Synaptic sees the mozilla package, perhaps???

Is the 3.0.6 nightly build I picked-up seen as a 3.1????
I see no other.

Dunno how I managed to get an en-gb package, tho... since it should be  en-us or somesuch.
 		                   		  		  		  		  		 		 			 				 				* 					 						[Last  edited by phubert28]("http://ubuntuforums.org/posthistory.php?p=9510851"); 24 Minutes Ago at 01:32 PM..  					 					 				*

---

### Post by manuelb on 2010-06-25
Could it be you tried an early release package from mozilla-daily ppa? tb3.1 alpha?

---

### Post by phubert28 on 2010-06-25
What I DID try came down as 3.0.6 nightly. Something I found on a Google search and followed-up TRYING to get 3.1. It's NAMED "Shredder" ... could be that.

But, under "about" it's shown as en-US, where the conflict is with an en-gb.

---

### Post by phubert28 on 2010-06-25
I saw a Thunderbird entry 1.3. something or other, en-gb suffix. Removed it, the install worked!

---

### Post by phubert28 on 2010-06-25
> It should replace the previous package, 3.0.5, but for some reason the  icon and the menu entry are lost: just pick an icon from your  "/usr/local/lib/thunderbird-3.1/chrome/icons/default" and you should be  done.
From now on, we should be able to "Check for updates" from the "Help"  menu

Well, no such dir. And under icons all that exists is "updater.png"

---

### Post by phubert28 on 2010-06-25
So far, although I found a thunderbird-bin, I haven't been able to find anything that will RUN the new Thunderbird...

I had mail open!!!

So, now I've got some screwy icon in my launcher bar... (shrug)

**

And, of course I'm in the line of those waiting for a compatible Lightning plug-in!

---

### Post by phubert28 on 2010-06-25
Found the icons under thunderbird-3.1 > chrome > icons > default

---

### Post by giorgosts on 2010-06-27
@phubert28
If you have kde4 like me, in order to have your new thunderbird listed under Applications>Internet, you should
```
ln -s -t .local/share/applications/ /usr/share/app-install/desktop/thunderbird.desktop
```
I suppose there should be an equivalent for gnome menu too

---

### Post by phubert28 on 2010-06-27
No, I'm running Gnome... vanilla 64 bit Ubuntu 10.4.

But, I'll save that command!

Thanks!

---

### Post by roger64 on 2010-07-01
I am a French. I use Lucid and I like using debs and eating French fries.

To get TB 3.1, this is not as easy as it looks. Ubuntuzilla and some others probably provide TB 3.1 debs but they are not easily localized. The easiest way to localize a Mozilla package is probably quick_locale_switcher, but it does not support (yet) TB 3.1. 

So I had to forget about my deb and install the official version. It was finally much easier than I expected. 

Once downloaded on my desktop, I uncompressed it with a right click and got a Thunderbird folder. 

I moved it to /opt where I have already somme outside programs. 
sudo mv /home/user/Desktop/Thunderbird /opt/

Then I clicked on the item called Thunderbird in the Thunderbird folder (tricky, eh?) to see if it was working. It did.

So, I modified the entry to Main Menu regarding Thunderbird and I modified the email item path in System/Preferences/Preferred Applications
both to: /opt/Thunderbird/Thunderbird 

And that'it...

I used Synaptic to uninstall the Thunderbird from Ubuntu. Of course, I kept the profile alive.

---

### Post by FrancoNero on 2010-07-05
so what's the status on that rapidshare .deb file that was posted. can that safely be installed? is that a true 64bit tb 3.1 final? what are the known issues, and more importantly, why can't mozilla just provide such .deb files, seems that it's not so hard to make them.... O:)

---

