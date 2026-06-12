---
title: "Lots of warnings"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-04-20
What should I do about all this....??

pr 21 09:42:01 PJKING gnome-session[4061]: EggSMClient-WARNING: Desktop file '/home/pj/.config/gnome-session/saved-session/10d3d9dccfe293aa4a123753956088412700000042880049.desktop' has malformed Icon key 'skype.png'(should not include extension) 
Apr 21 09:42:01 PJKING gnome-session[4061]: WARNING: Could not parse desktop file /home/pj/.config/autostart/xfconf-migration-4.6.desktop: Key file does not have key 'Name' 
Apr 21 09:42:01 PJKING gnome-session[4061]: WARNING: could not read /home/pj/.config/autostart/xfconf-migration-4.6.desktop 
Apr 21 09:42:02 PJKING gnome-session[4061]: WARNING: Could not parse desktop file /home/pj/.config/autostart/xfce4-settings-helper-autostart.desktop: Key file does not have key 'Name' 
Apr 21 09:42:02 PJKING gnome-session[4061]: WARNING: could not read /home/pj/.config/autostart/xfce4-settings-helper-autostart.desktop 
Apr 21 09:42:13 PJKING gnome-session[4061]: WARNING: Could not parse desktop file /etc/xdg/autostart/update-notifier-kde.desktop: Key file does not have key 'Type' 
Apr 21 09:42:13 PJKING gnome-session[4061]: WARNING: could not read /etc/xdg/autostart/update-notifier-kde.desktop 
Apr 21 09:42:29 PJKING gnome-session[4061]: WARNING: Could not launch application '10baccdf2aa6f45746124022396831082600000040820058.desktop': Unable to start application: Failed to execute child process "deskbar-applet" (No such file or directory) 
Apr 21 09:42:29 PJKING gnome-session[4061]: WARNING: Could not launch application '10baccdf2aa6f45746124022385145614100000040820008.desktop': Unable to start application: Failed to execute child process "search" (No such file or directory) 
Apr 21 09:43:00 PJKING NetworkManager: <WARN>  list_connections_cb(): Couldn't retrieve connections: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken..

---

### Post by juancarlospaco on 2009-04-20
Debug messages, because you have more than one Desktop environtment, doesn't matter for end user.

---

### Post by dunbrokin on 2009-04-21
Thanks

---

