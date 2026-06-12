---
title: "How do you install Scribus?"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by Edward B. on 2009-08-11
I've been to the Scribus page, but I can't quite figure it out. Do I need to download every package [here]("http://debian.scribus.net/debian/")? 

Or is there an easier way to do this?

Thanks!

---

### Post by arochester on 2009-08-11
Scribus is available from repository. Connect to the internet, open a Terminal and input the command: sudo apt-get install scribus

---

### Post by mcduck on 2009-08-11
Or got to Applications->Add/Remove, make sure it's set to display all available packages and then do a search for scribus, or browse under the graphics-section. When you find it, just mark the checkbox and click "apply".

You should probably read this to get rid of the Windows-way of downloading programs from web sites: [http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by meho_r on 2009-08-13
Maybe OT is referring to the new 1.3.5.1 version (or 1.3.5.0) which is not available through repo yet. However, there is a package on [getdeb.]("http://www.getdeb.net/app/Scribus")

---

### Post by SirWeazel on 2009-08-14
I too am looking for the best way to install the latest version (1.3.5.1). I'm wondering if the best way is to install the .deb file, or to add it to the repository (which detailed instructions would help).  Also, will one way overwrite the allready installed one, or update it?  There is a developmental release in the the add/remove manager, but from the description it doesn't sound like the latest release. Thank you for any help given.

---

### Post by colau on 2009-08-16
> **Edward B. said:**
> I've been to the Scribus page, but I can't quite figure it out. Do I need to download every package [here]("http://debian.scribus.net/debian/")? 

Or is there an easier way to do this?

Thanks!
```

sudo aptitude install scribus

```

---

### Post by Edward B. on 2009-08-20
Thanks a lot guys!

I have to say that these forums are the best I've come across as far as receiving quick and helpful answers.

And Scribus looks like exactly what I've been looking for - a low-cost (even better, it's free!) replacement for a basic version of InDesign.

Thanks again!

---

