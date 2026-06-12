---
title: "Uninstall Crossover Office"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by groeswenphil on 2009-02-06
The website says I should delete these folders.

~/cxoffice
 ~/.cxoffice
 /opt/cxoffice

Either I can't find them, they aren't there, or I'm looking in the wrong place.

What shoould I do?

Phil

---

### Post by taurus on 2009-02-06
What are the outputs of these commands from a terminal?

```
ls -la ~
ls -la /opt
```

---

### Post by groeswenphil on 2009-02-06
First one is :-

---

### Post by taurus on 2009-02-06
I suppose you don't remember where you installed it.

What's the output of this command from a terminal?

```
sudo find / -name cxoffice -print
```

---

### Post by groeswenphil on 2009-02-06
Does nothing.....just flashes a cursor at me.
Phil

---

### Post by taurus on 2009-02-06
Are you sure you installed Publisher 97 with CrossOver Office, not wine?

---

### Post by groeswenphil on 2009-02-06
Yes..............and everything worked right up until the end when it threw up a couldn't alter the registry error.

Phil

---

### Post by howefield on 2009-02-06
Publisher isn't even mentioned on the Crossover site, and doesn't get a great mention on the Wine database , the best being a bronze rating for 2003

Not to say it won't work but...

---

### Post by groeswenphil on 2009-02-06
[COLOR="Magenta"][SIZE="6"]It's OK. I've got Publisher 97 working in WINE........It won't load its own templates but it is loading and printing my old files.

Going out to get drunk now.

Phil[/SIZE][/COLOR]

---

### Post by LowSky on 2009-02-06
I hope Phil is using a newer version of Ubuntu because 6.06 is out of date when it comes to availible applications

also getting drunk and using Giant Pink Lettering isn't cool, unless you bring beer for everyone

;)

---

### Post by groeswenphil on 2009-02-06
Using 8.10
Still sober though.

Publisher does appear to be working well though.

Phil

---

