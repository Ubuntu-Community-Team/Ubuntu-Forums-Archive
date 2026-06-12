---
title: "pdf"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by demalan on 2009-06-18
I want to do my income tax on sarsefiling.co.za (South Africa). I don't know if this can be done on ubuntu/firefox. I know that it can be done on windows/ firefox. You need Adobe pdf on the system and then the browser opens with an integrated pdf where you can fill in your tax form online and submit. When I try to do this, I get the message that the latest version of pdf is not on my system. In any way it looks like here on ubuntu it try to downloud the income tax form apart from the web browser which is wrong because then I would not be able to edit and submit again. Or is this jus not possible to be done in ubuntu?

---

### Post by rsgangr on 2009-06-18
The *.pdf reader in Ubuntu cannot open the SARSefiling file and neither can the older versions of Adobe Reader (prior to about Version 8, I think) for Windows. In both cases you will need to install an updated version.

For Ubuntu I have just downloaded and installed "AdbeRdr9.1.0-1_i486linux_enu.bin". It is able to open a SARS *.pdf file that I saved a few months ago but I have not yet tested it online with the SARS database. I shall be testing it live within the next month, once I have received all my IT3(b) documents.

Good luck!

---

### Post by kwacka on 2009-06-18
try the mozilla-acroread plugin - it's in the medibuntu repository. You may also need the acroread-escript plugin.

---

### Post by Ms_Angel_D on 2009-06-18
I'm guessing but I think you should be able to install adobe reader from synaptic and then go into firefox preferences under the applications tab and set pdf to other then browse to and select /usr/bin/acroread

Good Luck ;)

---

### Post by ellgor on 2009-06-18
Hi,

Its easier to install Adobe's PDF app, than go round in circles. Use synaptic and install an app called "gdebi" (it might already be installed) next use your browser and go to the Adobe site and click on the appropiate app you want, do not download the default one presented instead click on "Different language or operating system" in the new window presented click on "Select an OS" from the drop down menu choose Linux-86 (deb) and download it. Obviously save it to somewhere you know where it will be and once it has downloaded go the place where it is, right click on the package and choose open with gdebi (if not already highlighted) it will then install itself and be ready to use, if for some reason there are some packages that it says it needs take note and download them with synaptic and then retry, hope this helps.

Regards, Ellgor.

---

### Post by demalan on 2009-06-18
> **ellgor said:**
> Hi,

Its easier to install Adobe's PDF app, than go round in circles. Use synaptic and install an app called "gdebi" (it might already be installed) next use your browser and go to the Adobe site and click on the appropiate app you want, do not download the default one presented instead click on "Different language or operating system" in the new window presented click on "Select an OS" from the drop down menu choose Linux-86 (deb) and download it. Obviously save it to somewhere you know where it will be and once it has downloaded go the place where it is, right click on the package and choose open with gdebi (if not already highlighted) it will then install itself and be ready to use, if for some reason there are some packages that it says it needs take note and download them with synaptic and then retry, hope this helps.

Regards, Ellgor.

Thanks a million
Done that and it works like a charm.
David

---

### Post by ZADixie on 2010-05-25
@Ellgor,

I also want to thank you. It works! Now I can compete and print my EMP201 forms.

---

