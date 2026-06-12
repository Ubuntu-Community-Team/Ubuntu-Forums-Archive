---
title: "Jaunty Theme repository?"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by MaxVK on 2009-06-15
I found a few really nice looking themes for Jaunty, but it appears that there is a repository to add, and paranoia abounding, I thought Id ask here to see if anyone knows anything about these themes (and of course how safe/valid the repository is)

The themes can be found [here]("http://francois.vogelweith.com/index.php?Itemid=23"). You need to click on each theme image to see that a repository needs to be installed.

For a very quick look at what needs to be done you can also read about it [here]("http://www.unixmen.com/linux-distributions/ubuntu/265-great-themes-for-ubuntu-904-jaunty-jackalope")

Information or advice anyone?

cheers

Max

---

### Post by rogueleader12345 on 2009-06-15
Don't know about that, but take a look at gnomelook.org they have some good stuff, lots of themes, safe and reliable.

---

### Post by jimv on 2009-06-15
It's fine, but I didn't care for any of the themes once I installed them.

---

### Post by MaxVK on 2009-06-15
rogueleader12345: Yes, I know gnomelook.org, I just happened across these and wondered if they were safe to use etc - I don't like to just add an unknown repository.

jimv: Thanks for that. Any specific reason why you didn't like them, or just not your taste?

cheers

Max

---

### Post by CatKiller on 2009-06-15
If you're unsure about a repository, you can always check it out without adding it to sources.list. Just peek about with a web browser. If there are packages that you are suspicious about - unexpected SSH stuff or whatever - then you'll know not to upgrade those packages. You could also grab some packages at random and open them in Fileroller to see what files they'll install. You might also want to do an upgrade before you add the repository so that you know that any new packages come from the new repository.

---

### Post by Cheesemill on 2009-06-15
I've used these repos in the past with no problems

---

### Post by jimv on 2009-06-15
A matter of taste :)

---

### Post by SOULRiDER on 2009-06-15
> **CatKiller said:**
> If you're unsure about a repository, you can always check it out without adding it to sources.list. Just peek about with a web browser. If there are packages that you are suspicious about - unexpected SSH stuff or whatever - then you'll know not to upgrade those packages. You could also grab some packages at random and open them in Fileroller to see what files they'll install. You might also want to do an upgrade before you add the repository so that you know that any new packages come from the new repository.

I was going to suggets the same thing, although you can never be sure how safe a repo is.

---

### Post by CatKiller on 2009-06-15
> **SOULRiDER said:**
> I was going to suggets the same thing, although you can never be sure how safe a repo is.

There was a case, quite a while ago now, where someone who hosted a (suddenly-)popular third-party repository started hosting replacement packages for ubuntu-wallpapers amongst other things, so that anyone that updated those packages without paying attention got a black background with a stern warning about how third-party repositories could be hosting anything, and that updating without thinking about it was putting an enormous amount of trust in some random bloke on the Internet. That kept people guessing for a little while.

As with most things, a little bit of common sense goes a long way. The Ubuntu community is pretty large, so problems with the official repositories are likely to be picked up and corrected quickly. The same isn't necessarily true of other repositories.

EDIT: [This]("http://ubuntuforums.org/showthread.php?t=297814") was the pretty large thread on this forum about it. [This]("http://www.flickr.com/photos/trevi55/296804891/") is the image that was put as the desktop wallpaper for those users who were using those repositories.

---

### Post by MaxVK on 2009-06-16
Thanks for the input everyone. I am always a little dubious about installing anything that is not in the standard repositories, and it never hurts to get second opinions. I think that perhaps the unthinking installation of whatever takes your fancy is probably where most Windows users get caught out - I was always a paranoid when I used Windows, and I think thats probably the best thing that I bought with me to Ubuntu.

Now then, CatKiller (and possibly someone else), when you say check the repository out before adding it to the sources.list, how exactly do I do that? Can the repository be downloaded as a file? If so I didn't realise that - I thought that it was added to sources.list and then was available from synaptic - I didn't realise you could inspect it quite so closely.

Thanks everyone

Regards

Max

---

### Post by Cheesemill on 2009-06-16
To check out the repository simply type in its URL into your browser, it's
[http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/)
for the theme repository in question.

You can now just have a browse around and inspect the contents of files before choosing to add it (or not) to your sources.list

---

### Post by MaxVK on 2009-06-16
Thanks Cheesemill, I didn't know that.

regards

Max

---

