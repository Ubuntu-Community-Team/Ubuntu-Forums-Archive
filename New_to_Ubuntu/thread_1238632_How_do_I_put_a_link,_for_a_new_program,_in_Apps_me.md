---
title: "How do I put a link, for a new program, in Apps menu?"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by Dnyce2k6 on 2009-08-12
I'm relatively new to Ubuntu. When I download a program, its usually a tar file so I just right click and select extract here. Fine, I understand that. But once its downloaded how do I make a spot for it in the applications menu? 

For instance, I just recently installed Vuse, and now I have to open a folder on my desktop and select the Vuse link everytime I want to use it. This is kinda lame and I know there must be some way to put it in the Apps menu. I figured it would automatically be under Internet or Sound/Video but it isn't. Any suggestions?

---

### Post by terry_gardener on 2009-08-12
right click applications, click edit menus, click new item

---

### Post by mbzn on 2009-08-12
Rather install apps from Add/remove under Applications menu, if you cant find it there try searcing for the .deb files when you download. 
This is not a answer to your question but a sollution to your problem. tarballs has a complicated way to install, so i'd suggest to do the above...

Hope it helps

---

### Post by Dnyce2k6 on 2009-08-12
Okay, I'll be sure to look for .deb files in the future, thanks. But in regards to Vuze, the install link at the web site only seems to offer a .tat.bz2 file. :confused:

---

### Post by fballem on 2009-08-12
> **Dnyce2k6 said:**
> Okay, I'll be sure to look for .deb files in the future, thanks. But in regards to Vuze, the install link at the web site only seems to offer a .tat.bz2 file. :confused:

I might be missing something, but is there a reason that you would not install Vuze from the repositories?

The reason that I ask is that installing from the repositories is the easiest and safest way to install an application - and there is a version of vuze in the repository.

You did say that you were relatively new to Linux. One of the advantages that Linux has over Windows is that under normal circumstances, you do not go hunting all over the web for applications - the first stop should always be the repository. To access the ubuntu repository, select System > Administration > Synaptic Package Manager. Once that's open, then you can search for the application that you want. If it is there, then mark it for installation and then Apply. The application will be installed, along with any required dependencies, and normally, there will be an item added in the appropriate place on the Application menu.

Hope this helps,

---

### Post by Dnyce2k6 on 2009-08-12
Actually, I did type Vuse in Synaptic and got no results. Now I just tried "Azureus" and it showed up. Nevertheless, the other options are still good to know. Thanks to everyone. I suppose my last question should be how do I mark my problem as "Solved"? :)

---

### Post by CatKiller on 2009-08-12
> **Dnyce2k6 said:**
> Actually, I did type Vuse in Synaptic and got no results.

That might be the problem. It's vu**z**e :) It's in the Universe repository, which you can enable with the Software Sources tool.

---

### Post by Dnyce2k6 on 2009-08-12
> **CatKiller said:**
> That might be the problem. It's vu**z**e :) It's in the Universe repository, which you can enable with the Software Sources tool.


Yiiiiiiiikes. Lol, we all make mistakes. Right? :)

---

