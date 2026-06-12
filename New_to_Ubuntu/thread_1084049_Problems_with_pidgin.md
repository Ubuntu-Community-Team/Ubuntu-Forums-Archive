---
title: "Problems with pidgin"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by omni504 on 2009-03-01
I use pidgin to sign into msn (and only msn). I was using it for the longest without any trouble until today..... Whenever i try to message someone, it freezes up and i have to force quit pidign. Any ideas what could be causing that?

---

### Post by kpmoore on 2009-03-01
Not sure. Have you tried reinstalling it using the Synaptic Package Manager?

---

### Post by brundles on 2009-03-01
> **omni504 said:**
> I use pidgin to sign into msn (and only msn). I was using it for the longest without any trouble until today..... Whenever i try to message someone, it freezes up and i have to force quit pidign. Any ideas what could be causing that?

Which version of Ubuntu are you using?

I'm using 8.10 and think there is a problem with the build they've used of the MSN plugin for Pidgin. I can use Yahoo and GMail all day long without any issues, but MSN first loses the audio notifications after a while then keels over and dies.

---

### Post by sneeks on 2009-03-01
have you tried amsn?

---

### Post by llamabr on 2009-03-01
Post the output of ```
pidgen -v
```

You might do well to update your version if it's true that there's a bug with msn.

---

### Post by tehforum on 2009-03-01
> **llamabr said:**
> Post the output of ```
pidgen -v
```

You might do well to update your version if it's true that there's a bug with msn.

Do you mean "pidgin"?

---

### Post by ibuclaw on 2009-03-01
There are no issues with the version I'm running:
```

$ pidgin -v
Pidgin 2.4.3

```

Though, the version in Intrepid appears to be 2.5.2...

Regards
Iain

---

### Post by brundles on 2009-03-01
> **sneeks said:**
> have you tried amsn?

Actually, that's a point - I'm using the WLM plugin rather than the straight MSN Plugin after MS made some changes that broke the original one. Could be specific to that - worth a play around with.

As for the -v:
keith@HTPC:/etc/init.d$ pidgin -v
Pidgin 2.4.1

*Edit:* Just to confuse things, a pidgin -v gives the 2.4.1 above, but the About menu option from Pidgin reports 2.5.2.

---

### Post by ibuclaw on 2009-03-01
[EDIT]
How did this double post happen ? :/

---

### Post by tehforum on 2009-03-02
> **brundles said:**
> Actually, that's a point - I'm using the WLM plugin rather than the straight MSN Plugin after MS made some changes that broke the original one. Could be specific to that - worth a play around with.

As for the -v:
keith@HTPC:/etc/init.d$ pidgin -v
Pidgin 2.4.1

*Edit:* Just to confuse things, a pidgin -v gives the 2.4.1 above, but the About menu option from Pidgin reports 2.5.2.

How do I upgrade without losing all my groups, and other settings?

---

