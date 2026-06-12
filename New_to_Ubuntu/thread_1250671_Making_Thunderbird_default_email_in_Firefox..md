---
title: "Making Thunderbird default email in Firefox."
date: 2009-08-26
forum: New to Ubuntu
---

### Post by servicetech on 2009-08-26
How do I make Thunderbird automatically open when I click on an email link? Thunderbird isn't an option in the listed applications in Firefox. Thunderbird and Firefox work fine by themselves.

---

### Post by MyR on 2009-08-26
did you set tbird in system > prefs > preferred apps?

peace

---

### Post by servicetech on 2009-08-26
I have the options of thunderbird or mozilla thunderbird in the preferences, neither option is in the firefox options. Where is the "exe file" located in the ubuntu file system? I could just manually add in Firefox if I knew where the "start file" was.

---

### Post by MyR on 2009-08-26
> **servicetech said:**
> I have the options of thunderbird or mozilla thunderbird in the preferences, neither option is in the firefox options. Where is the "exe file" located in the ubuntu file system? I could just manually add in Firefox if I knew where the "start file" was.

```
myr@truthlife:~$ whereis thunderbird
thunderbird: /usr/bin/thunderbird ...
```

so /usr/bin/thunderbird is the "start file". typically /usr/bin contains application launchers.  hope this helps!

peace

---

### Post by MyR on 2009-08-26
> **servicetech said:**
> I have the options of thunderbird or mozilla thunderbird in the preferences, neither option is in the firefox options. Where is the "exe file" located in the ubuntu file system? I could just manually add in Firefox if I knew where the "start file" was.

just to be clear.. you know I was talking about the system menu on your ubuntu panel, not in firefox settings, right?

---

### Post by servicetech on 2009-08-27
Yes I know you meant in the preferred applications

The USR/bin file fixed the issue in Firefox :)
Thanks !!!

---

