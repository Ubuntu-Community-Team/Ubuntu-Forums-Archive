---
title: "Login screen unavailabe after installing new pymouth"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by lng on 2011-08-11
[SIZE=2][COLOR=Black]Sir/Madam,

I Installed SPINFINITY Plymouth theme over my old text theme. I took help from a Web Tutorial.
I succeeded to install the theme, but after the Animation of the theme Screen goes blank.
I had to edit some files to install the same.How can I Fix this problem ?


Thank You.
[/COLOR][/SIZE]

---

### Post by wojox on 2011-08-12
Have you tried this?

[Plymouth themes: Fix, install, create in Ubuntu 10.04 (Lucid Lynx)]("http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html")

---

### Post by lng on 2011-08-12
[SIZE=2]Its not that i want to change the plymouth. after installing the plymouth, I am unable to use my UBUNTU OS.
after selecting the OS plymouth loads & then - instead of showing LOGIN Screen- screen goes blank.
Could i Revert that Plymouth change from UBUNTU Boot CD. . . .??
I am using Internet from CD Boot.[/SIZE]

---

### Post by wojox on 2011-08-12
What Web Tutorial did you use?

---

### Post by lng on 2011-08-15
Right now I hav somehow managed to get into my UBUNTU on the harddisk.
logged in from Root & then gave

> sudo/etc/initd/gdm restart
then i reverted whatever i did earlier.
Now I hav no Plymouth. Just those start-up codes.
don't hav the link to the toutorial.
i ll tell watever i did.

> sudo update-alternatives --config default.plymouth

selected the theme, but didn't work.

> sudo rm /etc/initramfs-tools/conf.d/splash
gksu gedit /etc/grub.d/00_header

replaced
> if loadfont `make_system_path_relative_to_its_root "${GRUB_FONT_PATH}"` ; then
  set gfxmode=${GRUB_GFXMODE}
  load_video
  insmod gfxterm
fi

with,

> if loadfont `make_system_path_relative_to_its_root "${GRUB_FONT_PATH}"` ; then
  set gfxmode=${GRUB_GFXMODE}
  set gfxpayload=keep
  load_video
  insmod gfxterm
fi

> sudo update-grub
sudo update-alternatives --config default.plymouth

atlast

> sudo update-initramfs -u
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u
sudo update-grub
                     
                                                                              this did the trick, bt got Screwed as mentioned earlier.

I would like to know, why i got that problem  and if possible,
install the plymouth theme without any problem

Thank you sir.

---

