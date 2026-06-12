---
title: "uninstalled gmail notifier with synaptic&gt; still in indicator applet"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by nityabaddha on 2010-08-07
Hi guys, i am total newbie and only been using lucid lynx for a few days . I installed a program called Gmail notifier and decided to uninstall it using synaptic package manager but it is still running in the indicator applet from evolution. The 'google mail' in the menu doesnt work but it still notifies me when there is new mail. How do i remove this program completely? Thanks in advance.

Hare Hare:p

---

### Post by Legendary_Bibo on 2010-08-07
You could try going to synaptic again, and when you go to remove it, use 'Complete Removal'

or you could try
```
purge *program_name*
```

---

### Post by nityabaddha on 2010-08-08
> **Legendary_Bibo said:**
> You could try going to synaptic again, and when you go to remove it, use 'Complete Removal'

or you could try
```
purge *program_name*
```

Hi and thanks for your reply. I am finidng that it is not marked as installed in synaptic manager. And there is only option to 'mark for install'. The purge command doesnt work in my terminal. 


No command 'purge' found, did you mean:
 Command 'pudge' from package 'python-pudge' (universe)
 Command 'ipurge' from package 'kolab-cyrus-common' (universe)
 Command 'ipurge' from package 'cyrus-common-2.2' (universe)

Hare Hare

---

### Post by nityabaddha on 2010-08-08
I restarted my machine and it seems to have disappeared somehow. I'm not sure how. I'm such a newbie. If there is a name for new newbie, i'd be that.

---

### Post by themusicalduck on 2010-08-08
If you uninstall any program while it is running then it will stay running until you quit it. So restarting the PC would have just quit the program.

---

### Post by nityabaddha on 2010-08-08
So how should i proceed.Kitty meow...

Hare Hare

---

### Post by nityabaddha on 2010-08-08
I guess maybe i was a little unclear in my description. i rebooted a few times after installing and it was still in the evolution indicator applet. 

Forgive my ignorance

Hare Hare

---

### Post by themusicalduck on 2010-08-08
Ok, still not sure what you meant by 'it disappeared'. Do you mean it went from Synaptic?

What program exactly is it you installed? I have a Gmail notifier, but for it to be in the messaging menu, you have to actually run it (it's a python script) and I have it set to run on startup.

In fact, it might be worthwhile checking your startup applications to see if there's anything in there related to the notifier.

meow

---

