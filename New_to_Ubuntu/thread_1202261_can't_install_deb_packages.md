---
title: "can't install deb packages"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by camaron1 on 2009-07-02
For the last couple of days i've been unable to install deb packages either from the internet or a cd or whatever. I get an error message (please see attachment). I've not change any preferences (and I don't know what preferences it refers too)

Any help welcome

Thank you

---

### Post by Sub101 on 2009-07-02
Its not really a solution but ive always found that I cannot install debs by downloading with open with it supplying the same message you have.

I have to "Save as" then open from the download location.

---

### Post by camaron1 on 2009-07-02
> **Sub101 said:**
> Its not really a solution but ive always found that I cannot install debs by downloading with open with it supplying the same message you have.

I have to "Save as" then open from the download location.

Thanks for quick response.

For some reason I thoght I'd tried that already,but it seems I hadn't because it works as you said, thanks. Still, as you say, is not the best solution so if someone knows why this has happened...

---

### Post by ellgor on 2009-07-02
Hi,

You need a package called "gdebi" available through synaptic, its specific for installing deb files, hope this of use.

Regards, Ellgor.

---

### Post by ~sHyLoCk~ on 2009-07-02
What does it show when you do ```
sudo dpkg -i packagename.deb
```

---

### Post by sadaruwan12 on 2009-07-02
> **camaron1 said:**
> For the last couple of days i've been unable to install deb packages either from the internet or a cd or whatever. I get an error message (please see attachment). I've not change any preferences (and I don't know what preferences it refers too)

Any help welcome

Thank you

Hi,

Just right click on a .deb file and go to open with tab from there select the default package opening program as GDebi Package Installer if it's not there then install it from the Synaptic Package Manager. 'Cos I had the same problem earlier this fixed it till I decided to do a clean install of my OS.

---

