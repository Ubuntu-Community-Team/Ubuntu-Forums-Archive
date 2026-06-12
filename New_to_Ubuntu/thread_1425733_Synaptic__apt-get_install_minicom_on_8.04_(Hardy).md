---
title: "Synaptic / apt-get install minicom on 8.04 (Hardy)"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by Pierrot Lafouine on 2010-03-09
Well, I have a EeePC with Hardy (fresh installation)
and also a desktop with Hardy, upgraded from 6.10.

I'm trying to get minicom

The synaptic/apt get install minicom works fine on desktop (finds it)
The synaptic/apt get install minicom doesn't work on EeePC (doesn't find it)

Looking at Synaptic/Settings/Repository/ in both installation doesn't give
same windows/option.  On EeePC, it shows DialogBox with tabs (Ubuntu
Software/Third-Party Software etc...)  while on destop it shoes only a list
of repos with checkbox

Why the different behavior of the GUI ?
I need minicom on EeePC, but Synaptic does'nt find it.

Thanks

---

### Post by MichealH on 2010-03-09
Are they running the same version?

Have you downloaded minicom from the backports/multiverse?

Was the minicom from a custom PPA?

---

### Post by Pierrot Lafouine on 2010-03-09
> **MichealH said:**
> Are they running the same version?
Yes, 8.04 (Hardy

> **MichealH said:**
> Have you downloaded minicom from the backports/multiverse?
Was the minicom from a custom PPA?
I have no idea, what can I do/check to answer that ?

Thanks

---

### Post by MichealH on 2010-03-09
Goto System > Administration > Software Sources then cheack if the 4th tick is ticked On the laptop if not and the desktop has tick it and try again.

---

### Post by Pierrot Lafouine on 2010-03-09
Hi
On laptop : the fourth checkbox is checked.
On desktop : there are no Software Sources menu...!!!
(this PC use to have problem with menu)

How can I start it from command line ?

---

### Post by MichealH on 2010-03-09
Sorry I had to see it from the menu so You can run It like it was if you did it from the menu forgot the command doh!

But I searched hard for It and here it is:
```
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
```

---

### Post by Pierrot Lafouine on 2010-03-09
Sorry, but I don't know what to do with the last post :-(
I have copied paste the line into commandline, but nothing happened.
I have copied paste command into gksu dialog box, nothing.

Either something is broken, or I'm doing it wrong.  Juts provides little
more details, as I suspect I'm doing it wrong

Thanks

---

### Post by MichealH on 2010-03-09
> **Pierrot Lafouine said:**
> Sorry, but I don't know what to do with the last post :-(
I have copied paste the line into commandline, but nothing happened.
I have copied paste command into gksu dialog box, nothing.

Either something is broken, or I'm doing it wrong.  Juts provides little
more details, as I suspect I'm doing it wrong

Thanks

OOps my fault... I am running Karmic and I gove you the karmic one ](*,)

---

### Post by Pierrot Lafouine on 2010-03-09
> **MichealH said:**
> OOps my fault... I am running Karmic and I gove you the karmic one ](*,)

Looks like its not your fault.
I look into this folder : /usr/share/applications/
And they are no software source application on Desktop
But their is a software source application on EeePC...

How do I get this software, Synaptic doesn't find it...!

---

### Post by Pierrot Lafouine on 2010-03-09
I don't understand...

I tried to install glibc-doc with synaptic on my EeePC, got this error
message : 
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc-doc_..._all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc-doc_..._all.deb).
404 Not Found [IP:91.189...]

But it works on my desktop...
:???:

---

### Post by Pierrot Lafouine on 2010-03-09
Ok, 
I just hitted reload button on Synaptic, and now it works!!!
I don't understand how this kind of issues can happen.
But thank you very much MichealH for your time

---

### Post by MichealH on 2010-03-11
Ahh the wonders of 

sudo apt-get update

---

