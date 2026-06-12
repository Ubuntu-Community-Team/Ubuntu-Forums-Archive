---
title: "[SOLVED] Templates for glabels"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by nakama85 on 2008-12-02
Does anyone know where I can get full face Cd Stomper templates for glabels.

It has stomper templates but not full face?

---

### Post by nakama85 on 2008-12-02
Ok I figured it out.

I simply edited the xml file that contains the cd stomper template.

```
sudo gedit /usr/share/glabels/templates/misc-us-templates.xml
```

Find the following text.

>  CD STOMPER PRO CD Label Refills, (Face Only)                      * 
-->
&#8722;
<!--
 =================================================================== 
-->
&#8722;
<Template brand="Stomper" part="PRO CD" size="US-Letter" _description="PRO CD Labels 2-up (face only)">
<Meta category="label"/>
<Meta category="media"/>
&#8722;
<Label-cd id="0" radius="166.5" [COLOR="Blue"]hole="58.5"[/COLOR] waste="5">
<Markup-margin size="5"/>
<Layout nx="1" ny="1" x0="34" y0="43" dx="0" dy="0"/>
<Layout nx="1" ny="1" x0="245" y0="416" dx="0" dy="0"/>
</Label-cd>
</Template>

Then edit [COLOR="Blue"]hole="58.5"[/COLOR]
change it to [COLOR="Blue"]hole="25.5"[/COLOR]

Save the file and restart Glabels.
Pick the same Stomper template as before and it will now allow fullface printing.

Alternatively you could add another template all together with those settings.

*_Note:I finally figured out something all by myself with no help from the internet.....Sweet!!!!!!_*:guitar:

---

