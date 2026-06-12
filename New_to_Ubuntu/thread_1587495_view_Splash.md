---
title: "view Splash"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by Hippytaff on 2010-10-03
Trying to get a splash image working, is there any way I can test it without rebooting everytime?

not view the image btw, test to see if I've edited the debian theme file correctly - coz it aint working :-( (I'm probably being a moron again)

---

### Post by ajgreeny on 2010-10-03
I assume you are talking about a grub splash image, and not the old style usplash that showed during the boot process after grub.

If I'm right, show us the 05_debian_theme file to see if it's possible to find what is wrong.  It can certainly be done, I did it myself previously, but I don't even see the grub menu any more so I don't now bother.

If it's the old style usplash you want, I think you will be disappointed, as you can not do that with plymouth, and you can't un-install plymouth without completely messing up your system.

---

### Post by Hippytaff on 2010-10-03
it is grub2

```

source /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else
  WALLPAPER="/usr/share/images/grub/Moraine_Lake_17092005.tga"
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
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in /boot/grub/Moraine_Lake_17092005.tga`basename ${WALLPAPER}` ${WALLPAPER} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)        reader=png ;;
        *.tga)        reader=tga ;;
        *.jpg|*.jpeg)    reader=jpeg ;;
      esac
      if test -e /boot/grub/${reader}.mod ; then
        echo "Found background image: `basename ${bg}`" >&2
        use_bg=true
        break
      fi
    fi
  done
fi

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

```

I moved the image to /boot/grub as suggested by a tutorial because of encryption things

---

### Post by cariboo on 2010-10-03
You can set the path to the image in /etc/grub.d/05_debian_theme.

Once you've saved the file, in a terminal type:

```
sudo update-grub
```

your image should now show up on the grub screen.

---

### Post by drs305 on 2010-10-03
I currently don't have an old grub2 theme file with the "for i..." format. It changed and is now much easier with the "WALLPAPER=" convention.

Nevertheless, the snippet I have shows:
> 
for i in {/boot/grub,/usr/share/images/grub}/moreblue-orbit-grub.{png,tga} ; do 

whereas your's shows:
> 
  for i in /boot/grub/Moraine_Lake_17092005.tga[COLOR="Red"]`basename ${WALLPAPER}` ${WALLPAPER}[/COLOR] ; do


I am fairly sure that the type in red shouldn't be there, but don't know what was on the next line. Until I can find an archived script with the full contents I'm speculating.

What I can say is that when you have the path and code correct, when you run "sudo update-grub" you will see:
> 
Generating grub.cfg ...
Found background image: <some.image.name>

Until you see that line in the terminal, there isn't any point in rebooting to check as the image won't be there.

---

### Post by Hippytaff on 2010-10-04
Cheers everyone...will have a nother bash after work

---

