---
title: "rearranging grub2 menu entries"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by unitedoceanic on 2010-04-02
Hi there,

sorry to open up another grub2 topic, but unfortunately i can't understand grub2 (not even a bit).

i tried to follow [drs305's]("http://ubuntuforums.org/member.php?u=223945") grub threads but they are way to confusing for a beginner. 

my grub menu looks like this:

[LIST][*]Ubuntu, with Linux 2.6.32-19-generic[*]Ubuntu, with Linux 2.6.32-19-generic (recovery mode)[*]Memory test (memtest86+)[*]Memory test (memtest86+, serial console 115200)[*]Microsoft Windows XP Professional (on /dev/sda1)[/LIST]

and this is how i would like to have it:

[LIST=1][*]Ubuntu, 2.6.32-19-generic[*]Windows XP Professional[*]a brake line of some sorts[*]Ubuntu, 2.6.32-19-generic (recovery mode)[*]Memory test[*]Memory test, serial console)[/LIST]

---

### Post by undecim on 2010-04-02
To do that would require splitting up the /etc/grub.d/10_linux script that creates the Ubuntu entries.

I'll take a look at it and see what I can do...

---

### Post by undecim on 2010-04-02
Okay, this should do what you want. If you have any problems, post here to let me know.

Open a terminal and run these commands:

```
sudo cp -r /etc/grub.d /etc/grub.d.bak
cd /etc/grub
sudo cp 10_linux 35_recovery
sudo mv 20_memtest86+ 50_memtest86+
sudo cp 40_custom 33_divider

```

now, we need to modify 10_linux and 35_recovery to only show one menu entry each. Open them as root in your favorite text editor (press ALT+F2, and type "gksu gedit" if you don't have a favorite) 

Now, open /etc/grub.d/10_linux. Find and remove these lines:
```
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS}, Linux ${version} (recovery mode)" \
	"single ${GRUB_CMDLINE_LINUX}"
  fi
```

Save it, and next open /etc/grub.d/35_recovery and find and remove these lines:
```
  linux_entry "${OS}, Linux ${version}" \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
```

Next, open /etc/grub.d/33_divider and add this to the end:
```
menuentry "- - - - - - - - - - - -" {
}
```

Note that you can replace "- - - - - - - - - - - -" with whatever divider text you want to use.

And finally, run these two commands in a terminal:
```
sudo cp -r /etc/grub.d /etc/grub.d.new
sudo update-grub
```

If an update ever overwrites the changes you've made, you can always do this to restore it:
```
sudo rm -rf /etc/grub.d.bak
sudo mv /etc/grub.d /etc/grub.d.bak
sudo cp -r /etc/grub.d.new /etc/grub.d
sudo update-grub
```

---

### Post by oldfred on 2010-04-02
udecim's way will work just fine, but as with all things computer related there is more than one way:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)

/etc/default/grub
GRUB_DISABLE_OS_PROBER=true

---

