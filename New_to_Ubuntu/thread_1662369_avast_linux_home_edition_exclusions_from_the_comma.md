---
title: "avast linux home edition exclusions from the command line"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-01-08
$ avast -V
avast: avast v1.3.0
VPS: 110107-1 (date: 07.01.2011)
Copyright(C) 2003-2008. ALWIL Software. All rights reserved.

download from [http://www.avast.com/linux-home-edition#tab4](http://www.avast.com/linux-home-edition#tab4)

i know it has a gui with avastgui but i want it to run at early morning when i sleep so i need to set it as a cron job

avast -a -c --continue=31 /home/user -r=*/var/log/avast_loggs.txt

so how do i set the exclusions for the command line?

I have the exclusions set in ~/.avast/avastrc using the avastgui but they do not apply to the command line so how do i make them?

---

### Post by mikewhatever on 2011-01-10
You could try looking at 'avast --help' or 'man avast'.

---

