---
title: "How do I install this keyboard layout?"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by anilorac on 2009-07-08
I just installed Ubuntu a few days ago, and on Windows XP I used [this]("http://www.geocities.com/supertrasgu/") Spanish Dvorak layout (the second one); I don't like the that comes with ubuntu, the "h" and the "r" are switched and the signs in awkward places. 

It says that I have to remove the txt extension and copy the file in /etc/X11/xkb/symbols , but that folder doesn't exist and it doesn't let me create it.

---

### Post by unutbu on 2009-07-08
Backup the current es:
```

sudo cp /usr/share/X11/xkb/symbols/es /usr/share/X11/xkb/symbols/es.bak
```

Download [http://www.geocities.com/supertrasgu/downloads/es.txt and put it directly in /usr/share/X11/xkb/symbols:](http://www.geocities.com/supertrasgu/downloads/es.txt and put it directly in /usr/share/X11/xkb/symbols:)
```

sudo wget http://www.geocities.com/supertrasgu/downloads/es.txt -O /usr/share/X11/xkb/symbols/es

```

You should then be able to select the Spanish Dvorak layout through System>Pref>Keyboard

---

### Post by anilorac on 2009-07-09
> **unutbu said:**
> Backup the current es:
```

sudo /usr/share/X11/xkb/symbols/es /usr/share/X11/xkb/symbols/es.bak
```Download [http://www.geocities.com/supertrasgu/downloads/es.txt and put it directly in /usr/share/X11/xkb/symbols:]("http://www.geocities.com/supertrasgu/downloads/es.txt%20and%20put%20it%20directly%20in%20/usr/share/X11/xkb/symbols:")
```

sudo wget http://www.geocities.com/supertrasgu/downloads/es.txt -O /usr/share/X11/xkb/symbols/es

```You should then be able to select the Spanish Dvorak layout through System>Pref>Keyboard
I did this and I can't find it anywhere in the keyboard layouts list.

---

### Post by unutbu on 2009-07-09
Hm. Perhaps it is a permission issue. Please post the output of this command
```

ls -l /usr/share/X11/xkb/symbols/es
```
(Note in the command above, "-l" is a minus lowercase L, not a minus one.)

---

### Post by unutbu on 2009-07-09
So far my advice to you has been a bit shoddy. 
Hopefully this post will be an improvement. :)

Since last posting, I've downloaded and successfully installed [http://www.geocities.com/supertrasgu/downloads/es.txt](http://www.geocities.com/supertrasgu/downloads/es.txt).

To make the Spanish variant "DvorakMartinez1" available in System>Pref>Keyboard:

[list]
[*] Edit /usr/share/X11/xkb/rules/evdev.lst:```

gksu gedit /usr/share/X11/xkb/rules/evdev.lst
```
Search for "es: Dvorak" and change
```

  dvorak          es: Dvorak
```

to
```

  dvorak          es: Dvorak
  DvorakMartinez1 es: Dvorak Martinez
```

[*] Edit /usr/share/X11/xkb/rules/evdev.xml:
```
gksu gedit /usr/share/X11/xkb/rules/evdev.xml
```

Search for "Spain". Then search for "dvorak". Change
```

        <variant>
          <configItem>
            <name>dvorak</name>
            <description>Dvorak</description>
          </configItem>
        </variant>
```

to
```

        <variant>
          <configItem>
            <name>dvorak</name>
            <description>Dvorak</description>
          </configItem>
        </variant>
        <variant>
          <configItem>
            <name>DvorakMartinez1</name>
            <description>DvorakMartinez1</description>
          </configItem>
        </variant>

```
[/list]

See [http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11](http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11).

---

### Post by anilorac on 2009-07-09
It works now. Thank you **so** much!
There is no way I could have figured that out by myself.

---

