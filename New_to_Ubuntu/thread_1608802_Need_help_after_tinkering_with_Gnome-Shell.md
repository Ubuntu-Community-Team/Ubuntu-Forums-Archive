---
title: "Need help after tinkering with Gnome-Shell"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by AXBX7C on 2010-10-29
Hello all!

I should have known better but I executed the following command in my  terminal:
ln -s ~/gnome-shell/install/share/applications/gnome-shell.desktop ~/.local/share/applications/gnome-shell.desktop
gconftool-2 -s /desktop/gnome/session/required_components/windowmanager "gnome-shell" -t string

Seen here: [http://live.gnome.org/GnomeShell#Running_gnome-shell_at_the_start_of_your_session](http://live.gnome.org/GnomeShell#Running_gnome-shell_at_the_start_of_your_session)

Well, as you can imagine everything went wrong from now on... After doing this I only got a grey desktop after logging in. No icons or panels, whatsoever.

I tried to uninstall gnome-shell and reinstall the ubuntu desktop. However, I still have a weird window manager behavior. When I type 'metacity' into my terminal everything is working fine. Unfortunately I have to do this every time I log in... How can I get everything back to normal? Any help is greatly appreciated!

I'm not very keen on a complete reinstall of Ubuntu 10.04...

---

### Post by ironic.demise on 2010-10-29
I'm not sure how you can fix it but Gnome Shell is now in the Repos as far as I know.
```
sudo apt-get install gnome-shell
gnome-shell --replace
```

Try opening a terminal with ctrl+alt+t and installing gnomeshell and using it to replace whatever is going on.

or in terminal type ```
metacity --replace
```

---

### Post by AXBX7C on 2010-10-29
Oh well I've tried "metacity --replace"... It works as long as my terminal is open. Once I close it I have this weird behavior (everything is docked to the top panel, can't move windows...)

I don't want Gnome-shell I want back to Metacity ;-)

---

### Post by ironic.demise on 2010-10-29
Try ```
metacity --replace &
```
The ampersand forks the proccess to the background, then you can close terminal.
At login screen make sure your environment is set to metacity, or the default ubuntu.

---

### Post by AXBX7C on 2010-10-29
Unfortunately this doesn't work... When I do "metacity --replace &" and then close the terminal everything falls back to weird behavior. When I log-in I can only choose my session (Gnome, Gnome-failsafe, xterm) but no evironment...

---

### Post by AXBX7C on 2010-10-29
Hmm I thought I could give this a shot and it worked:

gconftool-2 -s /desktop/gnome/session/required_components/windowmanager "metacity" -t string
Well I'm not sure what I did but everything seems to be back at normal... Thx for your suggestions ironic.demise!

---

### Post by ironic.demise on 2010-10-29
Sorry, I don't know what that does either but glad it's back to normal.
I should warn you, don't try Unity quite yet, I did and got a similar result.

---

### Post by AXBX7C on 2010-10-30
Yeah I figured that... I guess Unity is not designed to work with Ubuntu 10.04...

---

### Post by ironic.demise on 2010-10-30
Wasn't it in the 10.10 Netbook edition by default?

---

### Post by Alcardil on 2011-03-02
> **ironic.demise said:**
> Wasn't it in the 10.10 Netbook edition by default?

yes it was. the good thing was the 10.10 Netbook remix gave you the option of logging in to Ubuntu Desktop as well.

---

