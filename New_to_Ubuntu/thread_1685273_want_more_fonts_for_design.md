---
title: "want more fonts for design"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by kapi on 2011-02-10
I installed gimp at work on a windows pc and have a good selection of fonts but I seem to be missing several fonts when I use ubuntu at home, any ideas please.

---

### Post by mcduck on 2011-02-10
Then download some fonts you like, or copy them from your other machines. You can simply put the .ttf files into ~/.fonts (or /usr/share/fonts if you want to install them for all users)

---

### Post by coffeecat on 2011-02-10
> **kapi said:**
> I installed gimp at work on a windows pc and have a good selection of fonts but I seem to be missing several fonts when I use ubuntu at home, any ideas please.

Which fonts? If you mean standard MS fonts such as Times New Roman, Arial, Verdana, etc then you can install the package ttf-mscorefonts-installer.

---

### Post by cipherboy_loc on 2011-02-10
Use the following command show a list of all available font packages:

```
apt-cache search "ttf-"
```

Further, you could then use something like:

```

dpkg --list > dpkg.cache

for i in `apt-cache search "ttf-" | sed 's/ - .*//g' | sed '/^$/d'`; do
        LINE=`grep -i " $i " ./dpkg.cache`
        if [ "$LINE" != "" ]; then
                STATUS=`echo "$LINE" | grep -io '^[a-z]\{1,\} ' | sed 's/[^a-z]//g'`
                if [ "$STATUS" == "ii" ]; then
                        echo "$i: installed"
                else
                        echo "$i: not installed"
                fi
        fi
done

rm dpkg.cache


```

To list all packages that contain the word "ttf" in their description or name.

Cipherboy

---

### Post by kapi on 2011-02-10
> **mcduck said:**
> Then download some fonts you like, or copy them from your other machines. You can simply put the .ttf files into ~/.fonts (or /usr/share/fonts if you want to install them for all users)

Thanks, I was simply wondering why gimp came with a different set of fonts to those in linux, maybe it doesn't.

Anyway thanks for the help

---

### Post by mcduck on 2011-02-10
I'm pretty sure Gimp doesn't come with any fonts at all. It simply shows you whatever fonts you have installed on your computer (or whatever happened to come with your OS and other programs you have installed).

---

### Post by Perfect Storm on 2011-02-10
> **mcduck said:**
> I'm pretty sure Gimp doesn't come with any fonts at all. It simply shows you whatever fonts you have installed on your computer (or whatever happened to come with your OS and other programs you have installed).

This.

To install fonts you have downloaded eg. from a font site, simple double click on them and click "install".

Most applications looks first locally which fonts are available then they check system-wide.

---

