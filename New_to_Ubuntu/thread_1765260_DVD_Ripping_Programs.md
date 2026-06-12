---
title: "DVD Ripping Programs?"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-22
Hello, are there any good DVD ripping programs out there?  I am very, very, weak when it comes to compiling source code and have done a few extractions already and cannot for the life of me figure out where the programs went.  I do not even know where to look for them.  So with that in mind, is there a program in the "Ubuntu Software Center"that can do this?

---

### Post by terrykiwi83 on 2011-05-22
> **TAspr said:**
> Hello, are there any good DVD ripping programs out there?  I am very, very, weak when it comes to compiling source code and have done a few extractions already and cannot for the life of me figure out where the programs went.  I do not even know where to look for them.  So with that in mind, is there a program in the "Ubuntu Software Center"that can do this?

DVD Decrypter / DVD Shrink under WINE work good.

Also Handbrake, Acidrip, DVD:RIP and Devede are all solid rippers.

Hope this helps

---

### Post by TAspr on 2011-05-22
> **terrykiwi83 said:**
> DVD Decrypter / DVD Shrink under WINE work good.

Also Handbrake, Acidrip, DVD:RIP and Devede are all solid rippers.

Hope this helps

How do you install Wine?  Do you have to keep these under Ubuntu or in a folder somewhere?  Do you even need Windows?  I cannot even find Handbrake

---

### Post by terrykiwi83 on 2011-05-22
WINE I think is in the Ubuntu Software Packages by default, just search for it and install it. If not go here [http://www.multimediaboom.com/how-to-install-wine-in-ubuntu-11-04-natty-narwhal-ppa/]("http://www.multimediaboom.com/how-to-install-wine-in-ubuntu-11-04-natty-narwhal-ppa/")

- No You Don't Need Windows
- Wine will install DVD Decrypter / Shrink all by its self and usually create a shortcut on your desktop.

---

### Post by TAspr on 2011-05-22
> **terrykiwi83 said:**
> WINE I think is in the Ubuntu Software Packages by default, just search for it and install it. If not go here [http://www.multimediaboom.com/how-to-install-wine-in-ubuntu-11-04-natty-narwhal-ppa/](http://www.multimediaboom.com/how-to-install-wine-in-ubuntu-11-04-natty-narwhal-ppa/)

- No You Don't Need Windows
- Wine will install DVD Decrypter / Shrink all by its self and usually create a shortcut on your desktop.

Really...  Now that's what I am talking about.  No Windows???  How does it get away with it?

---

### Post by krapp on 2011-05-22
WINE = Wine is not an emulator. It's a compatibility layer. What that means I haven't the slightest idea.

---

### Post by JohnAStebbins on 2011-05-23
> **TAspr said:**
> I cannot even find Handbrake

[http://handbrake.fr/](http://handbrake.fr/)
[https://edge.launchpad.net/~stebbins/+archive/handbrake-releases](https://edge.launchpad.net/~stebbins/+archive/handbrake-releases)

---

### Post by TAspr on 2011-05-23
> **JohnAStebbins said:**
> [http://handbrake.fr/](http://handbrake.fr/)
[https://edge.launchpad.net/~stebbins/+archive/handbrake-releases]("https://edge.launchpad.net/%7Estebbins/+archive/handbrake-releases")


I am not experienced enough to deal with the .tar files.  Any equivalents to these?

---

### Post by cottfcfan on 2011-05-23
Add the following line to your software sources without quotes:
"ppa:stebbins/handbrake-releases"
Then go to synaptic, reload & search for Handbrake.

---

### Post by Grenage on 2011-05-23
> **krapp said:**
> WINE = Wine is not an emulator. It's a compatibility layer. What that means I haven't the slightest idea.

It means that Wine doesn't need to emulate CPU instructions.

+1 for handbrake.

---

### Post by oldos2er on 2011-05-23
I use k9copy, but Handbrake is good too.

---

### Post by Allavona on 2011-05-23
AcidRip is the software center. Its truly simple.

The default output is AVI and it places all rips in your home folder. (All options can be changed, of course)

Stick in the DVD and click start, go and grab a coffee.

---

### Post by HermanAB on 2011-05-23
Howdy,

I would say +1 for Acidrip.  There is probably nothing simpler.

However, most rippers use ffmpeg underneath and there is no reason why you cannot just read the ffmpeg man page and do it directly, especially since the man page contains a one line example for this purpose!

---

### Post by TAspr on 2011-05-23
> **cottfcfan said:**
> Add the following line to your software sources without quotes:
"ppa:stebbins/handbrake-releases"
Then go to synaptic, reload & search for Handbrake.

So, is "ppa:stebbins/handbrake-releases" used in general for any software releases?" Can I put a term after the /to search for updates?

---

### Post by cottfcfan on 2011-05-23
Yes its used to add "Handbrake" to your software, you can then download the program as normal from synaptic.
It will update itself automatically through your update manager.

---

### Post by TAspr on 2011-05-23
> **cottfcfan said:**
> Yes its used to add "Handbrake" to your software, you can then download the program as normal from synaptic.
It will update itself automatically through your update manager.

So this command is not limited to "handbrake"?  Is it the command I use for all individual updates just by replacing the file name aftert the quotations?

---

### Post by cottfcfan on 2011-05-23
I really don't understand what your saying.
Just click system/administration/software sources/other software/add and then paste in:
```
ppa:stebbins/handbrake-releases
```
click add source and then close.
If you then go into synaptic and click reload, on the left hand side "new in repository" will appear, go there and you will see Handbrake to install.

---

### Post by JohnAStebbins on 2011-05-23
> **cottfcfan said:**
> I really don't understand what your saying.
Just click system/administration/software sources/other software/add and then paste in:
```
ppa:stebbins/handbrake-releases
```
click add source and then close.
If you then go into synaptic and click reload, on the left hand side "new in repository" will appear, go there and you will see Handbrake to install.

An alternative way to add a PPA (which is documented in the PPA link I gave earlier, follow the "Read about installing" link)...
```

sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-gui handbrake-cli

```

You seem to be a little confused about what a PPA is.  PPA stands for "Personal Package Archive".  These are software archives that are not maintained directly by Canonical.  Canonical supplies services that makes it possible for third parties (e.g. handbrake) to create their own packages and host them on a server that integrates seamlessly into ubuntu's update manager.  So adding "ppa:stebbins/handbrake-releases" adds an archive to your system for installing and updating handbrake releases that are prepared by a handbrake developer (me in this case :P).

---

### Post by TAspr on 2011-05-23
> **cottfcfan said:**
> I really don't understand what your saying.
Just click system/administration/software sources/other software/add and then paste in:
```
ppa:stebbins/handbrake-releases
```
click add source and then close.
If you then go into synaptic and click reload, on the left hand side "new in repository" will appear, go there and you will see Handbrake to install.

To make things simple, can you use ppa:stebbins/handbrake-releases
 To make general updates and only chagne what is after the foward slash?  For example, ppa:stebbins/whatever-program-you-want-updated.  I am not sure how else to explain it.

---

### Post by JohnAStebbins on 2011-05-23
I should add, if you are ripping encrypted DVDs, you will also need to install libdvdcss.  Read this.
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
and this
[https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs](https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs)

---

### Post by cottfcfan on 2011-05-23
I see.
No you can't. Some sofware developers use ppas so we can have software that isn't in the repositories.
Handbrake is one of those.
Most of what we want is in the repos though.

---

### Post by TAspr on 2011-05-23
> **JohnAStebbins said:**
> An alternative way to add a PPA (which is documented in the PPA link I gave earlier, follow the "Read about installing" link)...
```

sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-gui handbrake-cli

```

You seem to be a little confused about what a PPA is.  PPA stands for "Personal Package Archive".  These are software archives that are not maintained directly by Canonical.  Canonical supplies services that makes it possible for third parties (e.g. handbrake) to create their own packages and host them on a server that integrates seamlessly into ubuntu's update manager.  So adding "ppa:stebbins/handbrake-releases" adds an archive to your system for installing and updating handbrake releases that are prepared by a handbrake developer (me in this case :P).

Thanks John.

---

### Post by eltonw on 2011-05-23
> **TAspr said:**
> Hello, are there any good DVD ripping programs out there?  I am very, very, weak when it comes to compiling source code and have done a few extractions already and cannot for the life of me figure out where the programs went.  I do not even know where to look for them.  So with that in mind, is there a program in the "Ubuntu Software Center"that can do this?
In the Ubuntu Software Center, OR if you run Synaptic. Do a search for DVD rip. You will get quite a few native linux apps that work. NO NEED to install WINE.

---

### Post by TAspr on 2011-05-23
> **eltonw said:**
> In the Ubuntu Software Center, OR if you run Synaptic. Do a search for DVD rip. You will get quite a few native linux apps that work. NO NEED to install WINE.

Thanks again!

---

### Post by TAspr on 2011-05-23
> **cottfcfan said:**
> Add the following line to your software sources without quotes:
"ppa:stebbins/handbrake-releases"
Then go to synaptic, reload & search for Handbrake.

Hmmm, this does nothing in the terminal.  I will stick to the update center's choices.

---

### Post by TAspr on 2011-05-23
> **JohnAStebbins said:**
> An alternative way to add a PPA (which is documented in the PPA link I gave earlier, follow the "Read about installing" link)...
```

sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-gui handbrake-cli

```You seem to be a little confused about what a PPA is.  PPA stands for "Personal Package Archive".  These are software archives that are not maintained directly by Canonical.  Canonical supplies services that makes it possible for third parties (e.g. handbrake) to create their own packages and host them on a server that integrates seamlessly into ubuntu's update manager.  So adding "ppa:stebbins/handbrake-releases" adds an archive to your system for installing and updating handbrake releases that are prepared by a handbrake developer (me in this case :P).


Well, this did not work as well according to the terminal..

---

### Post by terrykiwi83 on 2011-05-23
its sudo apt-get update and not add-get update :)

---

### Post by yetiman64 on 2011-05-23
> **TAspr said:**
> Hmmm, this does nothing in the terminal.  I will stick to the update center's choices.
It's not meant to go in terminal. To use go to System > Administration > Software Sources > Other Software Tab > Click the "Add" button, and copy and paste that line into the dialog box, click "Add source", close Software Sources and choose the "Reload" button.

The PPA for handbrake is now installed and Handbrake will be available in Synaptic.

---

### Post by TAspr on 2011-05-23
> **terrykiwi83 said:**
> its sudo apt-get update and not add-get update :)


Oh...hahah.  Just going by what I was instructed.  Too funny..

---

### Post by TAspr on 2011-05-23
> **yetiman64 said:**
> It's not meant to go in terminal. To use go to System > Administration > Software Sources > Other Software Tab > Click the "Add" button, and copy and paste that line into the dialog box, click "Add source", close Software Sources and choose the "Reload" button.

The PPA for handbrake is now installed and Handbrake will be available in Synaptic.

How do you do this in Natty 11.04?

---

### Post by terrykiwi83 on 2011-05-23
do what Stebbins said in terminal

```

sudo apt-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-gui handbrake-cli

```

that should work in Natty :)

---

### Post by yetiman64 on 2011-05-23
> **TAspr said:**
> How do you do this in Natty 11.04?

Ahh, caught me there :). Try looking for Synaptic from the search bar and go to the menu item, Settings > Repositories. This should be the software sources dialog equivalent in Natty.

---

### Post by TAspr on 2011-05-23
> **yetiman64 said:**
> It's not meant to go in terminal. To use go to System > Administration > Software Sources > Other Software Tab > Click the "Add" button, and copy and paste that line into the dialog box, click "Add source", close Software Sources and choose the "Reload" button.

The PPA for handbrake is now installed and Handbrake will be available in Synaptic.

Well, where do you find this in 11.04?

---

### Post by yetiman64 on 2011-05-23
> **TAspr said:**
> Well, where do you find this in 11.04?
Post No 32, open Synaptic, menu Settings choose the Repository submenu, this will give you "Software Sources".

---

### Post by TAspr on 2011-05-23
> **yetiman64 said:**
> Post No 34, open Synaptic, menu Settings choose the Repository submenu, this will give you "Software Sources".

ok, where do I go from here? Sorry, I am a little rusty and it is the first time I am using this.

---

### Post by yetiman64 on 2011-05-23
> **TAspr said:**
> ok, where do I go from here? Sorry, I am a little rusty and it is the first time I am using this.
The second tab in "Other Software" and follow previous instructions, you are in the correct place.

---

### Post by TAspr on 2011-05-23
> **yetiman64 said:**
> The second tab in "Other Software" and follow previous instructions, you are in the correct place.

Do I choose "Add Volume"  As well, do I choose the other choices for Canonical?

---

### Post by yetiman64 on 2011-05-23
> **TAspr said:**
> Do I choose "Add Volume"  As well, do I choose the other choices for Canonical?
That is because you have the Canonical Partner repo highlighted, not necessary for handbrake, just click on close and select "reload" from the following box.

Edit: you can go back in here at any time and add Canonical if you want.

---

### Post by TAspr on 2011-05-23
> **yetiman64 said:**
> That is because you have the Canonical Partner repo highlighted, not necessary for handbrake, just click on close and select "reload" from the following box.

Edit: you can go back in here at any time and add Canonical if you want.

I highlighted that canonical by mistake, but were is the reload button that you mentioned??

---

### Post by yetiman64 on 2011-05-23
> **TAspr said:**
> Whee is the reload button?
If you closed the Software Sources and didn't get the option of reload, go to the Reload button in Synaptic's main toolbar and click it. (Synaptic handles repos a bit different iirc).

Once the reload is complete type "handbrake" (without the quotes) in the search box.
You will want to install the handbrake-gtk package.

---

### Post by TAspr on 2011-05-23
> **yetiman64 said:**
> If you closed the Software Sources and didn't get the option of reload, go to the Reload button in Synaptic's main toolbar and click it. (Synaptic handles repos a bit different iirc).

Once the reload is complete type "handbrake" (without the quotes) in the search box.
You will want to install the handbrake-gtk package.

Got it!  Thanks a bunch.  

Let me ask you, is this the utility you use, where programs are not in the synaptic package manager following the same protocol?  Is this where .tar files or .tar.gz files go as well?

Another question, why is the reference to the handbrake files still in the "other Software" section.  I thought they would disappear after installing them?

As well, why did I not install the non .gtk file?

See from the pic, it is still there.

---

### Post by yetiman64 on 2011-05-23
> **TAspr said:**
> Got it!  Thanks a bunch.  

Let me ask you, is this the utility you use, where programs are not in the synaptic package manager following the same protocol? 

Yes if they are packaged as a PPA. 

You can (rather unsafely) download .deb files off the internet and install, just make sure you ABSOLUTELY trust the source if you do so.

This is for repositories maintained by Canonical and the community. You just added JohnStebbins PPA (personal package archive) to the list of repos available to you. Doing this allowed you to add the program Handbrake. Handbrake in the PPA is a packaged .deb file.


 > **TAspr said:**
> Is this where .tar files or .tar.gz files go as well?

No, they have to be extracted to your filesystem then processed with a few commands, typically, configure, make and install (or checkinstall for easier removal/management). This is known as compiling from source.
I advise against the use of .tar and .tar.gz files for a beginner, it can get messy real quick.
Here are two links for compiling from source if you are interested,
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

> Another question, why is the reference to the handbrake files still in  the "other Software" section.  I thought they would disappear after  installing them?

As well, why did I not install the non .gtk file?

See from the pic, it is still there.     1. The ppa left there will allow you to automatically receive updates for Handbrake.

2. The other one is for use with the command line (terminal). You could say it is for more advanced users (read "terminal diehards"). cli = command line interface

I noticed in one of your earlier pics you have the stebbins ppa listed twice, I have only one instance here. You may want to remove one to keep your sources list neat. But leave the other one ticked for updates. Just check they are both identical if you choose to tidy them up and that the second is not for source code, in which case leave both.

---

### Post by TAspr on 2011-05-23
> **yetiman64 said:**
> Yes if they are packaged as a PPA. 

You can (rather unsafely) downloaded .deb files off the internet and install, just make sure you ABSOLUTELY trust the source if you do so.

This is for repositories maintained by Canonical and the community. You just added JohnStebbins PPA (personal package archive) to the list of repos available to you. Doing this allowed you to add the program Handbrake. Handbrake in the PPA is a packaged .deb file.


 

No, they have to be extracted to your filesystem then processed with a few commands, typically, configure, make and install (or checkinstall for easier removal/management). This is known as compiling from source.
I advise against the use of .tar and .tar.gz files for a beginner, it can get messy real quick.
Here are two links for compiling from source if you are interested,
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

1. The ppa left there will allow you to automatically receive updates for Handbrake.

2. The other one is for use with the command line (terminal). You could say it is for more advanced users (read "terminal diehards"). cli = command line interface

I noticed in one of your earlier pics you have the stebbins ppa listed twice, I have only one instance here. You may want to remove one to keep your sources list neat. But leave the other one ticked for updates. Just check they are both identical if you choose to tidy them up and that the second is not for source code, in which case leave both.


[B][I]I noticed in one of your earlier pics you have the stebbins ppa listed  twice, 
You may want to remove one to keep  your sources list neat. But leave the other one ticked for updates.  
Just check they are both identical if you choose to tidy them up and  that the second is not for source code, in which case leave both.[/I][/B]

Well, I think I did that because of the failed commands, but how do I get rid of one of them?

---

### Post by yetiman64 on 2011-05-23
> **TAspr said:**
> [B][I]I noticed in one of your earlier pics you have the stebbins ppa listed  twice, 
You may want to remove one to keep  your sources list neat. But leave the other one ticked for updates.  
Just check they are both identical if you choose to tidy them up and  that the second is not for source code, in which case leave both.[/I][/B]

Well, I think I did that because of the failed commands, but how do I get rid of one of them?
Go to the same place in Synaptic, Settings menu, repositories submenu, Other software tab.

Check that both are identical (that the second one is not for source code- as is the case with some ppas). If both are identical, highlight the second instance and click the "remove" button at the bottom of the window.

---

