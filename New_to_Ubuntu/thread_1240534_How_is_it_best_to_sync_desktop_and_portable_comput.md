---
title: "How is it best to sync desktop and portable computers?"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by tahitiwibble on 2009-08-14
Hi guys,

I'm so embarassed to be here and still asking absolute beginner questions! but at an age which is way past having to start ...... I am now a "road warrior".

Please can someone suggest the easiest, foolproof way to sync between my desktop and my very recently acquired Everex "Step Note" (which doesn't seem to be such a hot deal now that I'm actually using it). The object of the exercise being to have identical machines both at home and away.

Thanks a million in advance.

---

### Post by j.bell730 on 2009-08-14
Is [this page]("http://www.thinkwiki.org/wiki/How_to_copy_a_Linux_installation") any good for you?

---

### Post by tahitiwibble on 2009-08-14
> **j.bell730 said:**
> Is [this page]("http://www.thinkwiki.org/wiki/How_to_copy_a_Linux_installation") any good for you?

It could very well be. Although I was hoping for a one step operation like I do with my trusty old Palm 650. Thanks for the link.

---

### Post by john stiles on 2009-08-14
Also take a look at rsync and the gadmin-rsync GUI. Rsync is a very powerful command line programme that many backup/sync programmes put a front end upon. It is what I use to back up my desk top and sync with my netbook. Whilst I would not call rsync foolproof, once you have mastered a few key commands and saved them as a gadmin profile it is pretty much sorted.

Also look at Unison. 

They should all be searchable in the repositories by synaptic.

---

### Post by j.bell730 on 2009-08-14
> **tahitiwibble said:**
> It could very well be. Although I was hoping for a one step operation like I do with my trusty old Palm 650. Thanks for the link.

Yea, but IMO dd might just be the best tool for it.

---

### Post by tahitiwibble on 2009-08-14
> **john stiles said:**
> Also take a look at rsync and the gadmin-rsync GUI. Rsync is a very powerful command line programme that many backup/sync programmes put a front end upon. It is what I use to back up my desk top and sync with my netbook. Whilst I would not call rsync foolproof, once you have mastered a few key commands and saved them as a gadmin profile it is pretty much sorted.

Also look at Unison. 

They should all be searchable in the repositories by synaptic.

Hmmm, that's all going to take a little while to digest and evaluate. Thank you.

---

### Post by tahitiwibble on 2009-08-14
> **j.bell730 said:**
> Yea, but IMO dd might just be the best tool for it.

dd? just what does that stand for?

---

### Post by j.bell730 on 2009-08-14
> **tahitiwibble said:**
> dd? just what does that stand for?

Dataset definition, I believe. [Here's]("http://en.wikipedia.org/wiki/Dd_%28Unix%29") more info on it if you need it, and there are instructions on the link I provided.

---

### Post by tahitiwibble on 2009-08-14
> **john stiles said:**
> Also take a look at rsync and the gadmin-rsync GUI. Rsync is a very powerful command line programme that many backup/sync programmes put a front end upon. It is what I use to back up my desk top and sync with my netbook. Whilst I would not call rsync foolproof, once you have mastered a few key commands and saved them as a gadmin profile it is pretty much sorted.

Also look at Unison. 

They should all be searchable in the repositories by synaptic.

John,

Should I be looking to install/try Unison or Unison GTK?

Thanks again,

Martin

---

### Post by john stiles on 2009-08-14
I did try and run synctoy under wine, but no joy. It is about the only thing I miss.

---

### Post by grappler on 2009-08-14
Do you really want to copy everything? This would suggest that you had identical hardware. Don't you really want to copy the directories you have created in your home directory. In that case I would suggest using unison. 

[http://www.cis.upenn.edu/~bcpierce/unison/]("http://www.cis.upenn.edu/%7Ebcpierce/unison/")

---

### Post by john stiles on 2009-08-14
The Unison GTK seems to have a graphic interface which may be the best place to start.

---

### Post by tahitiwibble on 2009-08-14
> **grappler said:**
> Do you really want to copy everything? This would suggest that you had identical hardware. Don't you really want to copy the directories you have created in your home directory. In that case I would suggest using unison. 

[http://www.cis.upenn.edu/~bcpierce/unison/]("http://www.cis.upenn.edu/%7Ebcpierce/unison/")

I really meant to say that I just need all my personal files to be available on both machines i.e. emails, work projects, etc. I use Xmarks for my bookmarks and passwords which is a godsend.

I'm gravitating rapidly towards Unison. Thanks for the suggestion.

---

### Post by tahitiwibble on 2009-08-14
> **john stiles said:**
> The Unison GTK seems to have a graphic interface which may be the best place to start.

Thank you.

---

### Post by tahitiwibble on 2009-08-14
Oh boy!! I just realized that I don't know how to make the two computers available to one another. Heeeeelp, please.

---

### Post by grappler on 2009-08-14
Set up the ssh server  on each machine:

sudo aptitude install openssh-server openssh-client

and tell unison - using the gtk interface - that you want to use ssh. 

I usually install public keys. This explains. 

[http://ubuntuforums.org/archive/index.php/t-30709.html](http://ubuntuforums.org/archive/index.php/t-30709.html)

That way you don't need to keep putting in passwords. And I also - on my LAN give every computer a static IP address.

---

### Post by tahitiwibble on 2009-08-14
> **grappler said:**
> Set up the ssh server  on each machine:

sudo aptitude install openssh-server openssh-client

and tell unison - using the gtk interface - that you want to use ssh. 

I usually install public keys. This explains. 

[http://ubuntuforums.org/archive/index.php/t-30709.html](http://ubuntuforums.org/archive/index.php/t-30709.html)

That way you don't need to keep putting in passwords. And I also - on my LAN give every computer a static IP address.

I'll work on all this over the weekend. Thanks for all your help ........ and have a good weekend!

---

### Post by tahitiwibble on 2009-08-23
> **john stiles said:**
> Also take a look at rsync and the gadmin-rsync GUI. Rsync is a very powerful command line programme that many backup/sync programmes put a front end upon. It is what I use to back up my desk top and sync with my netbook. Whilst I would not call rsync foolproof, once you have mastered a few key commands and saved them as a gadmin profile it is pretty much sorted.

Also look at Unison. 

They should all be searchable in the repositories by synaptic.

Hello one and all,

I'm using something called "Back in Time" and can't figure out how to find my destination folder on my laptop remote computer. All I see is my source computer in the drop-down menus. Can anyone help me out?

---

