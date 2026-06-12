---
title: "Keyboard layout / location not saving"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by celticbhoy on 2010-05-05
For some reason on my wifes account the keyboard keeps re-setting itslef to USA. No matter how many times I set it to UK and remove USA, it still goes to USA on the next boot.

How do I solve this for good?

---

### Post by Cowboybebop79 on 2010-05-05
sounds to me like a permission problem to me check system > administration > users and groups and see if your wifes login has the permission to change settings.

ps. is this in 9.10 karmic or 10.04 lucid

---

### Post by celticbhoy on 2010-05-07
> **Cowboybebop79 said:**
> sounds to me like a permission problem to me check system > administration > users and groups and see if your wifes login has the permission to change settings.

ps. is this in 9.10 karmic or 10.04 lucid

Using lucid from update (not clean install). All permissions are checked within her user account.

---

### Post by Cowboybebop79 on 2010-05-07
Open synaptic package manager and check if these two packages are installed

libgnomekbd4

libgnomekbd-common

if they are already installed mark them for re-installation and mark any upgrades as well do a restart and then change the keyboard settings and do another reset to see if it has stuck.

Hope this helps

---

### Post by celticbhoy on 2010-05-07
> **Cowboybebop79 said:**
> Open synaptic package manager and check if these two packages are installed

libgnomekbd4

libgnomekbd-common

if they are already installed mark them for re-installation and mark any upgrades as well do a restart and then change the keyboard settings and do another reset to see if it has stuck.

Hope this helps

Gave it a whirl & re-installed, but still no dice.

---

### Post by Cowboybebop79 on 2010-05-07
Ok ](*,) do you have an account and if so are you using the same keyboard with uk layout?

---

### Post by celticbhoy on 2010-05-07
Yeah my account works fine, using exactly the same hardware.

---

### Post by Cowboybebop79 on 2010-05-08
Ok in you login open your keyboard preferences in the layouts tab at the bottom there is a button to apply the layout system wide. Give it a go it sounds to me as though something has gone wrong this the user config files in your wifes login will check to see if there is a solution.

---

