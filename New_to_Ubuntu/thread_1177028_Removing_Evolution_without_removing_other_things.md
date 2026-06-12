---
title: "Removing Evolution without removing other things"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by Andy06 on 2009-06-03
Trying to remove evolution data server seems to affect half of ubuntu, like ekiga, gnome appelets, panels, ubuntu-desktop?

Why is this?

Isn't evolution-data-server/data-server-common part of the evolution package?

---

### Post by Periswell on 2009-06-03
I have realised this as well. I am not quite sure why it does this but I remember when I last tried to unintall it and my computer would not start up. I thinks its best to leave evolution-data alone. I do though have a theory as to why some of those programs do uninstall when you uninstall the evolution-data package. With the gnome-panel, when ubuntu is first installed, a little icon, next to the menu bar, between firefox and the help icon, on the upper panel is the button for evolution (you may of, like me, gotten rid of that). This might be the reason for gnome-panel uninstalling itself when you uninstall evolution-data as it may think it relies on it. Probably the same with the other programs.

And that is it, I am sorry I could not answer your question but I suggest you do not touch it as it broke my computer.

-joshua

---

### Post by Andy06 on 2009-06-03
Yeah, ever since I switched. I always look very very careful at every associated package that gets uninstalled when I remove something from synaptic. So much stuff is cross-linked.

---

### Post by keplerspeed on 2009-06-03
Evolution, being the default gnome email client (dont know why, I think its.... not as good as thunderbird) might explain why its all 'tied' in. If other packages depend on the evolution data package.. just have to live with it.

I recon ubuntu should use thunderbird as default email client. Just my vote.

---

### Post by Tholley on 2009-06-03
Yeah, the little time and date up at the top right is tied into Evolution too, so I just removed Ev from the panel and unchecked default and put Tbird there as my default email. I like the calender and weather thingy that goes along with the date and time, better that Thunderbirds calender.

---

### Post by Lightsaber™ on 2009-06-03
> **keplerspeed said:**
> Evolution, being the default gnome email client (dont know why, I think its.... not as good as thunderbird) might explain why its all 'tied' in. If other packages depend on the evolution data package.. just have to live with it.

I recon ubuntu should use thunderbird as default email client. Just my vote.

If Evolution is an email client, then why are other packages in Ubuntu so dependent on it? Can we make a seperate package for those packages dependent on Evolution so we can remove Evolution? wait hehe was that clear?

---

### Post by Celauran on 2009-06-03
> **Lightsaber™ said:**
> If Evolution is an email client, then why are other packages in Ubuntu so dependent on it? Can we make a seperate package for those packages dependent on Evolution so we can remove Evolution? wait hehe was that clear?

Evolution is far more than just an email client. Therein lies the problem.

---

### Post by Didius Falco on 2009-06-03
For those interested in starting with a bare-bones install of Gnome, read this thread. Be sure and note the warnings about what may be missing in the way of functionality:

[http://ubuntuforums.org/showthread.php?t=1129425](http://ubuntuforums.org/showthread.php?t=1129425)

Regards,

Didius

---

### Post by themadhatter on 2009-06-13
> **Andy06 said:**
> Trying to remove evolution data server seems to affect half of ubuntu, like ekiga, gnome appelets, panels, ubuntu-desktop?

Why is this?

Isn't evolution-data-server/data-server-common part of the evolution package?

Because someone in the Gnome project, decided to try to emulate Windows. As a result, Evolution is closely integrated into Gnome, much like Internet Explorer and Outlook Express are closely integrated into Windows. Ever notice how corporate desktops with Microsoft Outlook installed still have Outlook Express installed? It's still installed because you can't remove it. Which makes no sense, because if you have Outlook installed, you are never going to use Outlook Express. And of course Microsoft in their Big Brother mentality have decided that Internet Explorer is a critical part of the operating system. Why? It's only a web browser, and there are dozens of replacements, most of which offer far better speed and stability.

Tying Evolution into Gnome was a huge mistake in my opinion. In fact I will go so far as to call it spectacularly stupid. In the old days when no one used web based email it may have made some sense (but what about all of other email clients available, why not use one of them?), but today, it makes no sense at all. Evolution should be de-coupled from the Gnome project.
:popcorn:

---

