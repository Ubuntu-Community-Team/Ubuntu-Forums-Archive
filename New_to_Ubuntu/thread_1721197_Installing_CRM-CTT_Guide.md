---
title: "Installing CRM-CTT Guide"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by zolthar on 2011-04-04
Hi,

I am fairly new to Ubuntu and wanted to learn something different. I have some limited knowledge and to best describe is its like running on 5th gear at 30km/h uphill!

If someone knows of a guide they can point me to, that would be much appreciated, otherwise here is what I have done so far and stuck:

I managed to get the following done so far:
[LIST=1]
[*]Installed Ubuntu with LAMP
[*]Install SSH so that I can transfer from Windows
[*]Got to the CRM-CTT checkup page
[/LIST]

Now I have the following issues:
[LIST]
[*]PHP request order: The request order of PHP is not set correctly (should be GPC but is GP)
[*]Advanced PHP Caching support (APC): Not available
[*]GD Library: Not installed. You will not be able to generate pictures.
[*]Write access to config file: Not writeable
[/LIST]

Any assistance would be much appreciated unless Google can enlighten me before hand.


EDIT: Found solutions to the above and for anyone (but more than likely myself) that finds this article:
[LIST=1]
[*]Edit php.ini request_order="GPC"
[*]sudo apt-get install php-apc
[*]sudo apt-get install php5-gd
[*]sudo chmod 777 config.ini.php
[/LIST]

---

### Post by nab on 2011-07-02
Hi zolthar,

sorry for high-checking your tread, but I stumbled upon crm-ctt interleave and want to know how easy it is to fit your use when you would want to use it in following setup:

small in-house sample shop with 5 workers (simplified work-flow):

1) producing samples
-> incoming raw material
-> incoming inspection
-> decision on "manufacturing steps" (best case: drag & drop)
-> manufacturing (including documentation)
-> outgoing inspection 
-> rework (whole lot or partial lot)
-> transport to next department (whole lot or partial lot)

2) maintenance of production material
-> scheduled maintenance
-> unscheduled maintenance

What I want to do, is:
- to keep track off what samples are in the shop and at which position (using status?)
- to document the manufacturing of samples (because some of them come back months/ years later to be redone) and the quality of raw material and work done in our department
- to keep the time needed to document all this very low (by the workers who are working on these samples)

Unfortunately I have only a small budget for doing this (but at least I have a budget :-)).

TIA

---

