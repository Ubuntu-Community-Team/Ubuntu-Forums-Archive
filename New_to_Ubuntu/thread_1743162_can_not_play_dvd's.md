---
title: "can not play dvd's"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by flagrl on 2011-04-29
i can not play dvd's i just updated to 11.04 but even when i had 10.10 i could not play any dvd's. can yall help me figure out how to play DVD's

---

### Post by frogotronic on 2011-04-29
> **flagrl said:**
> i can not play dvd's i just updated to 11.04 but even when i had 10.10 i could not play any dvd's. can yall help me figure out how to play DVD's

In a terminal:

```
sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh
```

- CH

---

### Post by flagrl on 2011-04-29
it says Unable to locate package libdvdread3

---

### Post by frogotronic on 2011-04-29
Hi,

   You need to enable the proper repositories, and my command was a little out-of-date.

   **System>Administration>Software Sources**

   Under the "Ubuntu Software" tab, make sure all are checked, except "Source".  Under the "Updates" tab, make sure all are checked in the *Ubuntu Updates* section.

  Reload the repositories.

   Install [Medibuntu]("http://medibuntu.org/")

In a terminal:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Then, run this code:

```
sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu
```

Install the codecs:

```
sudo apt-get install ubuntu-restricted-extras vlc libdvdread4 libdvdcss2 libdvdnav4
```

Reboot.

You're good to go.

- CH    :popcorn:

---

