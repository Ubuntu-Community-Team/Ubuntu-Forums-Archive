---
title: "Keyboard Shortcuts"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by losciloop on 2008-12-20
Heya Guys.

First time post on the forums, so take it easy on me haha.

I am running compiz and have a problem with my keyboard shortcuts.  I have 4 workspaces running and can switch using my assigned shortcut.  But there is another option that allows me to hit a combination of keys to go to a specific desktop.  In the keyboard shortcut window it only allows me to setup said shortcut for workspaces 1 and 2.

How do I get it to recognize all 4 workspaces?

---

### Post by drs305 on 2008-12-20
losciloop,

By only two options, are you looking at compiz's Window Management, Bindings tab and see only Previous and Next options?

I think metacity might be able to help you out. If you open gconf-editor and drill down to apps/metacity/window_keybindings there are already unassigned presets for moving to 12 workspaces. You have to assign the key combinations.

To open gconf-editor:
```

gconf-editor /apps/metacity/window_keybindings

```

---

### Post by losciloop on 2008-12-20
thanks mate!

for some reason, on a prior install it recognized 2+ workspaces.  No idea what the difference is, but thanks

---

### Post by losciloop on 2008-12-20
uh oh!  I jumped to an early conclusion.

it won't recognize the changes I made.  How do I save the changes?  Everytime I reopen the config file it it back to the default settings

---

### Post by drs305 on 2008-12-20
> **losciloop said:**
> uh oh!  I jumped to an early conclusion.

it won't recognize the changes I made.  How do I save the changes?  Everytime I reopen the config file it it back to the default settings

Are you using an approved format? I just tried it with the entry " **<ALT>4** " to move to workspace 4 and it worked fine. It is also possible you are selecting a key combination that is already assigned.

---

### Post by losciloop on 2008-12-20
Yep,

I am using <Control><Alt>1, 2, 3, 4 to switch amongst the workspaces.  When I go into the configuration, it gives me the option to create shortcuts for 12 workspaces.

I have not assigned said keystrokes to anything else.  So they are free to use

Why doesn't it save the edits I made to the config file?

---

### Post by losciloop on 2008-12-20
> **drs305 said:**
> Are you using an approved format? I just tried it with the entry " **<ALT>4** " to move to workspace 4 and it worked fine. It is also possible you are selecting a key combination that is already assigned.

user error

I wanted to use the Keypad and all I had to do was insert a KP_ before the number

---

