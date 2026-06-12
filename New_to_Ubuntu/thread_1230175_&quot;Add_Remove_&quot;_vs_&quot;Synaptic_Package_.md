---
title: "&quot;Add Remove &quot; vs &quot;Synaptic Package Manager&quot;"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by motrax on 2009-08-03
Hi! I've been using Ubuntu for a few weeks now. I just wanted to know what's the difference between using the "add remove" under Applications menu and the Synaptic Package Manager. I guess both are front ends for apt, but then why have two different gui front ends?

---

### Post by theozzlives on 2009-08-03
> **motrax said:**
> Hi! I've been using Ubuntu for a few weeks now. I just wanted to know what's the difference between using the "add remove" under Applications menu and the Synaptic Package Manager. I guess both are front ends for apt, but then why have two different gui front ends?

Synaptic is more extensive and will remove conflicting software, Add/Remove is simpler and easier to use but not as complete.

---

### Post by motrax on 2009-08-03
I'm sorry I don't get what you mean. Will "Add Remove" not check for dependencies or conflicts? Like, when I was trying to install lxnm, Synaptic said that NetworkManager had to be removed. If I was doing the same with "Add Remove", would it have gone ahead and installed it anyway and screwed up my system?

---

### Post by Katalog on 2009-08-03
you're correct that they're both just two different front ends for aptitude, but The Add and Remove frontend presents new users with some common, frequently used, applications and provides a friendlier interface for noobies so they don't have to go searching through Synaptic looking for exactly what they want, all the while having to wade through huge lists of applications and libraries with weird sounding names that make things even more confusing than simply finding an app will with a simple definition, clicking the check box and hitting "Apply".

Just makes it more simple for people who are making the transition.

---

### Post by motrax on 2009-08-03
> **Katalog said:**
> you're correct that they're both just two different front ends for aptitude, but The Add and Remove frontend presents new users with some common, frequently used, applications and provides a friendlier interface for noobies so they don't have to go searching through Synaptic looking for exactly what they want, all the while having to wade through huge lists of applications and libraries with weird sounding names that make things even more confusing than simply finding an app will with a simple definition, clicking the check box and hitting "Apply".

Just makes it more simple for people who are making the transition.

Ahh ... I see. Thank you for clearing that up.

---

### Post by schauerlich on 2009-08-03
Add/Remove lists common applications like what you would find in your applications menu, listed with familiar names and sorted into various categories to find what you want easier. Synaptic lists things by package name and includes all packages, making it harder browse for apps, but gives you more control over what you download - and great if you're looking for a specific package but aren't quite sure what the name of it is.

---

### Post by Copernicus1234 on 2009-08-03
The fastest way to search for a package is probably this command though:

sudo apt-cache search <part of package name>

---

### Post by credobyte on 2009-08-03
Add/Remove will not allow you to edit meta info ( eg. package contains 5 other packages .. you can customize them only via Synaptic ).

---

### Post by colau on 2009-08-16
Synaptic looks easier/better!

---

