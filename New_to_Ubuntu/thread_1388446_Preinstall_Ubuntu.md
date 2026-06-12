---
title: "Preinstall Ubuntu"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by Ant59 on 2010-01-23
I want to sell machines with Ubuntu preinstalled. However I want to add my own packages, such as *ubuntu-restricted-extras *to the installation, so the customer has everything they would expect to have in Windows. Where do I stand legally about remixing and redistributing Ubuntu, and adding these packages?

---

### Post by d3v1150m471c on 2010-01-23
You can only sell the computer. You cannot sell the OS nor the software with it. So be careful how you market it. Another thing you might want to consider is if a customer breaks their computer and needs tech support, how exactly they're going to go about it. These days, it seems like having anything but the typical windows default OS will void the warranty.

---

### Post by Ant59 on 2010-01-23
Thanks for the quick reply!

I will be buidling and selling the computers. I want to install a slightly modified Ubuntu onto the machines, so they can be used out-of-the-box. I will be offering a choice of Ubuntu, or to pay to add Windows. I think I remember reading somewhere a few months ago, about naming when remixing Ubuntu :s

---

### Post by Ant59 on 2010-01-23
Please excuse the double post.

After a while, I cannot find anything to answer all of my question, so I'm going to email cannonical, and hopefully they can help me.

I am basically looking to do what system76 does, but I want to know where I stand legally about add packages to preinstalled ubuntu. If anyone can help, I would be very greatful.

---

### Post by 3rdalbum on 2010-01-23
> **d3v1150m471c said:**
> You can only sell the computer. You cannot sell the OS nor the software with it.

Yes you can. Take a look at [http://shop.canonical.com](http://shop.canonical.com) if you don't believe me!

Ubuntu-restricted-extras could pose some thorny problems. Flash Player cannot be redistributed without Adobe's permission (that's why the Flash Player package just downloads the plugin from the Adobe website). Java still requires you to accept its license, which the user would have to do. The Microsoft fonts are also restricted distribution and might even require the end-user to also have a Windows license.

You could set up the Medibuntu repository and then have a menu item called "Install proprietary software support" that invokes Synaptic to install "ubuntu-restricted-extras", "libdvdcss2" and "non-free-codecs". Libdvdcss2 is still a legal grey area though.

I'm not sure exactly how to invoke Synaptic to install only, but you could find out on the web or by looking at the source code for Jockey.

---

### Post by Ant59 on 2010-01-23
Thank you for your really useful reply!

That is a great idea, to add a menu item to install the packages.

As you seem knowledgable in this area, can you confirm where I stand legally about preinstalling Ubuntu, and still using the name "Ubuntu" and the logo for the altered installation?

I want too, to add Compiz and a few of the effects to the desktop as default.

---

### Post by philinux on 2010-01-23
How does linux mint get around the flash issue. Mint 8 has it integrated I see.

And java is preinstalled. In fact firefox comes with a load of plugins ready to go.

I dont use mint but was wondering how they get around this issue.

[http://linuxcritic.com/stories/43-Linux-Mint-8-Review-and-Commentary.html](http://linuxcritic.com/stories/43-Linux-Mint-8-Review-and-Commentary.html)

---

### Post by quinnten83 on 2010-01-23
you could try with remastersys, which is sipposed to allow you to adapt your install into an image.

---

### Post by Ant59 on 2010-01-23
Thanks for the reply Quinnten, but the remastering part won't be a problem. I just need to know the legal side of things.

---

### Post by cascade9 on 2010-01-23
> **philinux said:**
> How does linux mint get around the flash issue. Mint 8 has it integrated I see.

And java is preinstalled. In fact firefox comes with a load of plugins ready to go.

I dont use mint but was wondering how they get around this issue.

[http://linuxcritic.com/stories/43-Linux-Mint-8-Review-and-Commentary.html](http://linuxcritic.com/stories/43-Linux-Mint-8-Review-and-Commentary.html)

Mint is one of the distros that dont really care about legal issues. Not like its the only distro that comes with a lot of stuff that some distros dont. Check out sabayon, it comes with....well....everything preinstalled. Flash, mp3/other audio codecs, video codecs, DVD playing support, etc.

---

### Post by prenoob on 2010-01-23
> **Ant59 said:**
> Thanks for the reply Quinnten, but the remastering part won't be a problem. I just need to know the legal side of things.Really, I think you ought to take proper Legal Advice on what you can do.  The fact that you are*** selling** *software (as opposed to free redistribution) is going to have a big effect on some of the Licences.

---

### Post by Ant59 on 2010-01-23
I don't want to sell free software. I am selling hardware with free software pre-installed.

---

### Post by cascade9 on 2010-01-23
> **prenoob said:**
> Really, I think you ought to take proper Legal Advice on what you can do.  The fact that you are*** selling** *software (as opposed to free redistribution) is going to have a big effect on some of the Licences.

Not on GPL (or BSD for that matter)- 

> **Does the GPL allow me to sell copies of the program for money?**Yes, the GPL allows everyone to do this.  The [right to sell copies]("http://www.gnu.org/philosophy/selling.html") is part of the definition of free software.  Except in one special situation, there is no limit on what price you can charge.  (The one exception is the required written offer to provide source code that must accompany binary-only release.) 


[http://www.gnu.org/licenses/gpl-faq.html#DoesTheGPLAllowMoney](http://www.gnu.org/licenses/gpl-faq.html#DoesTheGPLAllowMoney)

---

### Post by Paddy Landau on 2010-01-23
> **3rdalbum said:**
> [QUOTE=d3v1150m471c;8710564]You can only sell the computer. You cannot sell the OS nor the software with it.Yes you can. Take a look at [http://shop.canonical.com](http://shop.canonical.com) if you don't believe me![/QUOTE]
Canonical is not selling Linux. It is selling support, training, the service of putting it onto a CD or DVD and mailing that to you, and merchandise. The operating system and associated software is still non-chargeable.

You will have no problem including Ubuntu as a *free* operating system included with your computer, especially if a proprietary system (Windows) costs extra.

On selling the computer, you can preinstall the various software, but have the customer sign (as part of the contract) that he accepts the various licenses; you would print them for the customer to read, and include them with the paperwork. That way, the customer gets the fully-working computer, and you have ensured acceptance of the license.

You might have to include the Ubuntu license, which (I believe) is that the customer may not charge for the software or for its distribution, including any derivatives.

It's a nice idea. I wish you good luck with it.

---

### Post by Ant59 on 2010-01-23
Thank you Paddy Landau.

This has explained a lot to me, and I think I now know how to go about this.

One last thing, if anyone can help: I read somewhere that there are tight rules on using the Ubuntu name on customized distros. **Does what I'm doing count as a distro (where I wouldn't be able to stil call it Ubuntu), or simply as just pre-installing programs, as manufacturers do with Windows?**

---

### Post by llawwehttam on 2010-01-23
As the software you are talking about pre-installing is all in the ubuntu repos you are not really modifying the underlying OS so I don't see that you are distributing a modified OS therefore I see no problem.

---

### Post by Ant59 on 2010-01-23
Thank you everyone, you've all been really helpful! I think I've got all the information I need now :)

---

### Post by HeadHunter00 on 2010-01-23
I think that it isn't illegal to modify it. Besides, it's better to get important packages preinstalled, than having a noob to look all around google to learn about ubuntu. Just don't change the repositories.

---

### Post by Ant59 on 2010-01-23
Thanks HeadHunter.

I definitely have my answers now and hopefully I can be selling Ubuntu machines soon :)

---

### Post by Ant59 on 2010-01-23
Please excuse the double-post again.

I've just thought of a few other things relevant to this.

Am I allowed to remove one of the GNOME Panels and replace it with Gnome-Do Docky? Or is this too much modification to still be labeled Ubuntu? Or do you think this is a little too far?

Other things I want to be able to do are:
- Add Compiz and enable a few of the effects
- Change the default desktop background
- Add shortcut to website in the system menu

---

### Post by Paddy Landau on 2010-01-23
> **Ant59 said:**
> Am I allowed to remove one of the GNOME Panels and replace it with Gnome-Do Docky? Or is this too much modification to still be labeled Ubuntu? Or do you think this is a little too far?
That's not a modification. You are not changing any code whatsoever. You're simply changing the settings and loading some extra programs.

> **Ant59 said:**
>  Other things I want to be able to do are:
- Add Compiz and enable a few of the effects
- Change the default desktop background
- Add shortcut to website in the system menu
Ditto.

When you take the code and modify it, that's modification. When you take the program and use it differently, that's just using it differently.

A car gives a metaphor. If you take a car, change the bodywork and install a different gearbox, that's modification. If you simply use the car on a racing track after painting it a different colour and changing the upholstery, that's just using it differently.

---

### Post by Ant59 on 2010-01-23
Awesome. Thank you very much for your help.

---

### Post by The Cog on 2010-01-23
I have read that on the issue of your obligation under the GPL to provide access to the source code, people like yourself who merely install someone else's distro rather than modifying th ecode yourself can simply provide a link to the distro where you acquired the software. So providing a link to the Ubuntu repos will (I think, IANAL) meet your legal obligations.

I was going to refer you to efficientpc.co.uk who have sold PCs with Ubuntu installed for some years, but sadly they have closed down. Their web site says too many others are also selling Linux preinstalled these days. I wish you better luck with your endevours.

---

### Post by Ant59 on 2010-01-23
Thanks Cog.

I will most likely be selling the machines with a booklet, with an introduction to Ubuntu, as most customers will have never come across Ubuntu before. In there I want to include links and acknowledgements to everything useful and Ubuntu-help-related, including the Ubuntu project site, so I guess this covers me. I will also include a link to the Ubuntu site and the ubuntuforums.org site on the desktop of the new-installs.

I have still got a lot to think about before offering Ubuntu machines, but at least I know I'm covered legally now.

---

### Post by lila on 2010-01-24
Hello,

...I just stumbled across this thread... check out these guys: 
I bought a new computer a few weeks ago, from [www.i-ventive.com](www.i-ventive.com) , it's a small French company in a suburb of Paris, and they do just that: sell computers with Ubuntu as the default install, all ready to turn, Flash, quite a few codecs (although shop-bought DVDs don't seem to be covered), and the wonderful experience of unpacking your new computer, plugging in the various cables, switching it on, and - everything works, and much better than I ever had any computer of mine working. :popcorn: The install is finished, except it still asks you to choose your language and set your user name and password (fair enough...)
They seem to do well with what they do, so I'm sure there is a market for it in the UK as well.

How they do legally, I don't know, but maybe you can ask them? It would surprise me if they don't speak English.

Anyway, for those of us (like me) who use computers as a means to an end and just use Ubuntu because it's, free, legal, and, well, nice to use, it's definitely the way to go to get computers from shops like that - they end up cheaper of course, no license fee for Windows, and no endless research and worrying over "is it going to be compatible with Ubuntu?"

So good luck to you!:P

All the best, lila

---

### Post by Ant59 on 2010-01-24
Thanks Lila :) It's reassuring to know it can be done. I will probably get in contact with them.

---

### Post by carbonbased on 2010-01-24
> **Ant59 said:**
> Thanks Lila :) It's reassuring to know it can be done. I will probably get in contact with them.

Companies have been doing what you're talking about for years. Go here and you'll find many distros that mix apps under different licenses into their distro: [http://distrowatch.com/](http://distrowatch.com/)

Read the licenses, talk to the distro's creators. There are so many like you describe, do you really need to create your own?  Look at [http://distrowatch.com/table.php?distribution=pclinuxos](http://distrowatch.com/table.php?distribution=pclinuxos), for example.

Talk to some distro people about using theirs on your pcs.

---

### Post by Ant59 on 2010-01-24
I have created my own distro before. I am not interested in that. I wanted to know how much I can modify Ubuntu and still use the name.

---

