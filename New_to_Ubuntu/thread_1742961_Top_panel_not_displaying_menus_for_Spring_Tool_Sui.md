---
title: "Top panel not displaying menus for Spring Tool Suite"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by arun170682 on 2011-04-29
I recently installed ubuntu 11.04 on compaq presario. It is working fine in all other aspects except one. I installed Spring Tool Suite for Java development but the menu-bar( i.e. file , edit, project etc.) are not present on top panel as it is present for other application(i.e. firefox). For Spring Tool Suite only 'Window' menu is present. 

I also installed eclipse to check whether the problem also persist for eclipse also, but eclipse works perfectly fine and all menus are present in top panel.

I prefer Spring Tool Suite over Eclipse so could anyone please  help in this regard.

Thanks in advance.

Arun170682

---

### Post by beew on 2011-04-29
In Unity, in order to add tray icons to the panel you need to explicitly whitelist them. This is another pain brought to you because of the global menu. 
[http://www.omgubuntu.co.uk/2011/03/how-to-hide-or-show-app-tray-applets-in-ubuntu-11-04/](http://www.omgubuntu.co.uk/2011/03/how-to-hide-or-show-app-tray-applets-in-ubuntu-11-04/)

---

### Post by arun170682 on 2011-04-29
Thanks for quick reply.

My problem is with menus in Spring Tool Suite. Like Music Player or any application they contains menus in top panel for saving, printing and for other task there should be menus for Spring Tool Suite.

These menus are present for eclipse, but missing in Spring Tool Suite. There is only one menu present([COLOR="Red"]Window[/COLOR]) instead of about 10 menu headings (please refer attachment).

The attached screenshot is for Spring Tool Suite installed on Ubuntu 10.10. The problem I am facing is on Ubuntu 11.04.


Is there any setting which will enable remaining menus.

Thanks in advance.

Arun170682.

---

### Post by angelillo on 2011-05-02
I get the same behaviour. In my case, Unity panel only shows the Edit, Window and Refactor menus.

There are several bugs open in Launchpad reporting this issue:

[https://bugs.launchpad.net/ubuntu/+source/libdbusmenu/+bug/618587](https://bugs.launchpad.net/ubuntu/+source/libdbusmenu/+bug/618587)
[https://bugs.launchpad.net/appmenu-gtk/+bug/613119](https://bugs.launchpad.net/appmenu-gtk/+bug/613119)
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/655694](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/655694)

As a workaround, some people suggested to launch STS with the following command:

```

UBUNTU_MENUPROXY=0 /path/to/STS

```

This will make the menu appear in the STS window, not in the Unity panel.

---

