---
title: "cannot change panel properties in Lucid"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by appliedmath on 2010-04-30
Hello,

On fresh installation of Lucid, I tried to change panel properties using gconf-editor.  However, I could not find apps/panel/top_levels.  The only thing I could find is apps/panel/default_setup/top_levels/<panel names>, changing which does not affect anything I could immediately see.  Any help on this one?  I simply could not figure it out or google it.  I am trying to disable panel animation and set hide size to 0 pixel.

Thanks.

---

### Post by madjr on 2010-04-30
[http://www.omgubuntu.co.uk/2010/04/ubuntu-tweak-054-released-with-lucid.html](http://www.omgubuntu.co.uk/2010/04/ubuntu-tweak-054-released-with-lucid.html)

---

### Post by appliedmath on 2010-04-30
it would be nice if I get to know what the underlying mistake on my part is.

---

### Post by ankspo71 on 2010-04-30
I have apps/panel/top_levels on my install, but since you don't, I think it is because apps/panel/top_levels might be created only after you modify your panels somehow, so they are no longer using the default configuration. My panels are slightly modified, so therefor my panel can't use the default config. So try adding or removing something the panel, then go back into gconf-editor to see if apps/panel/top_levels shows up.
Hope this helps.

---

### Post by appliedmath on 2010-04-30
Thanks for your help.  I have changed things in the panel and also created new panels.  Still no show.  I had exactly this problem as well with 9.10, and I could not resolve it.  Now that I freshly installed 10.04 (with formatting the hard drive), I am having the same issue.

My other computer with also freshly installed 10.04 has the same issue.

---

### Post by appliedmath on 2010-04-30
> **madjr said:**
> [http://www.omgubuntu.co.uk/2010/04/ubuntu-tweak-054-released-with-lucid.html](http://www.omgubuntu.co.uk/2010/04/ubuntu-tweak-054-released-with-lucid.html)

I tried it, and it still did not fix my problem.

---

### Post by Sandiep on 2010-04-30
did it work in Karmic?

---

### Post by appliedmath on 2010-04-30
> **Sandiep said:**
> did it work in Karmic?

In karmic, I never bothered to fix.

---

### Post by appliedmath on 2010-04-30
> **appliedmath said:**
> Hello,

On fresh installation of Lucid, I tried to change panel properties using gconf-editor.  However, I could not find apps/panel/top_levels.  The only thing I could find is apps/panel/default_setup/top_levels/<panel names>, changing which does not affect anything I could immediately see.  Any help on this one?  I simply could not figure it out or google it.  I am trying to disable panel animation and set hide size to 0 pixel.

Thanks.


I am just a fool: I by habit typed sudo when starting gconf-editor in the terminal.  Starting gconf-editor without sudo works just fine.

---

