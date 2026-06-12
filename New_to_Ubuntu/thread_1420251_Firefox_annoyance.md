---
title: "Firefox annoyance"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by CBR_Rob on 2010-03-02
Every time I click in the address bar or search bar in Firfox on Ubuntu it places the cursor right where I clicked and does not highlight the whole address or search to left you type over. Is there a setting to change this?

---

### Post by ubudog on 2010-03-02
> **CBR_Rob said:**
> Every time I click in the address bar or search bar in Firfox on Ubuntu it places the cursor right where I clicked and does not highlight the whole address or search to left you type over. Is there a setting to change this?

Double click?

---

### Post by asmoore82 on 2010-03-02
Yes!!

This is an intentional behavior ~
it's one of the UI differences between Windows and Linux builds of Firefox.
The logic is that Linux users are much more likely to use the keyboard shortcut "F6"
to highlight the whole address, and more likely to expect precision with the mouse click.

To change this behavior, enter "about:config" in the address bar and
click through the warning prompt. You are now at a "registry editor" of sorts
for ***_ALL_*** Mozilla settings, even archaic ones that don't have any effect on Firefox.

Type "urlbar" into the "Filter" at the top, the key you are looking for is
browser.urlbar.clickSelectsAll, it's a simple boolean value,
so you can double click to toggle it to **true**.

You can look up almost any key name in there at [http://kb.mozillazine.org/About:config_entries](http://kb.mozillazine.org/About:config_entries)

---

### Post by CBR_Rob on 2010-03-02
Thanks for that info.

---

### Post by empty_spaces on 2010-03-02
Type **about:config** in the firefox url bar. Click ok view all configuration settings.

Type **browser.urlbar.clickSelectsAll** in the filter and double click it to change it's value to **true**. This should select all on single click.

Type **browser.urlbar.doubleClickSelectsAll** in the filter and double click it to change it's value to **false**. This should insert the cursor on double-click.

Edit: Sorry, slow typer

---

