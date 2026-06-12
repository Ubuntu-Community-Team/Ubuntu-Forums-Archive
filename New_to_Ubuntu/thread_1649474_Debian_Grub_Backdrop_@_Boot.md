---
title: "Debian Grub Backdrop @ Boot"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by fleamour on 2010-12-20
I installed XFCE4 & seem to have a Debian backdrop when Grub boots now.  How do I go back to black?

---

### Post by fleamour on 2010-12-20
This is my /etc/grub.d/05_debian_theme.  output:

> #!/bin/sh -e

. /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else
  WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"
  COLOR_NORMAL="black/black"
  COLOR_HIGHLIGHT="magenta/black"
fi

set_mono_theme()
{
  cat << EOF
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
EOF
}

# check for usable backgrounds
use_bg=false
for output in ${GRUB_TERMINAL_OUTPUT}; do
  if [ "$output" = "gfxterm" ] ; then
    for i in /boot/grub/`basename ${WALLPAPER}` ${WALLPAPER} ; do
      if is_path_readable_by_grub $i ; then 
        bg=$i
        case ${bg} in
          *.png)		reader=png ;;
          *.tga)		reader=tga ;;
          *.jpg|*.jpeg)	reader=jpeg ;;
        esac
        if test -e /boot/grub/${reader}.mod ; then
          echo "Found background image: `basename ${bg}`" >&2
          use_bg=true
          break
        fi
      fi
    done
    break
  fi
done

# set the background if possible
if ${use_bg} ; then
  prepare_grub_to_access_device `${grub_probe} --target=device ${bg}`
  cat << EOF
insmod ${reader}
if background_image `make_system_path_relative_to_its_root ${bg}` ; then
  set color_normal=${COLOR_NORMAL}
  set color_highlight=${COLOR_HIGHLIGHT}
else
EOF
fi

# otherwise, set a monochromatic theme for Ubuntu
if ${use_bg} ; then
  set_mono_theme | sed -e "s/^/  /g"
  echo "fi"
else
  set_mono_theme
fi

There are lots of guides for changing Grub2's splash screen, but no concise instructions for reverting to black.

---

### Post by fleamour on 2010-12-25
BUMP!!!

Can I comment this line with a hash?

```
WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"
```

---

### Post by fleamour on 2010-12-25
Although I can navigate to:

/etc/grub.d/05_debian_theme.  

& see contents, opening file as gksudo/sudo in nano or gedit just generates a blank page?

EDIT:

" ... If the file is not found, gedit will open a blank file with the file name entered on the command line: ... Note graphical applications use gksudo rather than sudo. ..."

So:

```
gksudo gedit /etc/grub.d/05_debian_theme
```

No full stop at end, hash comment appropriate line & bingo bango...(Hopefully no ugly Debian backdrop.)

---

### Post by fleamour on 2010-12-25
```
sudo update-grub
```

The missing piece of the puzzle...

---

