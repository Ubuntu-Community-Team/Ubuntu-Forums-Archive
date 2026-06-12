---
title: "firefox themes"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by dzon65 on 2010-03-12
Could someone tell me where firefox themes are located in karmic?

---

### Post by bluelamp999 on 2010-03-12
You have Firefox Personas - [http://www.getpersonas.com/en-US/](http://www.getpersonas.com/en-US/)

And you have Firefox Themes - [https://addons.mozilla.org/en-US/firefox/browse/type:2](https://addons.mozilla.org/en-US/firefox/browse/type:2)

---

### Post by dzon65 on 2010-03-12
?? I think you misunderstood.Where are they stored.I need the css of an installed theme.

---

### Post by ubu newb on 2010-03-12
Should be in the same place as using firefox under windows: Tools>options and under the general tab choose manage add ons.

---

### Post by dmillard10 on 2010-03-12
Try looking under ~/.mozilla/firefox, if you're looking for files relating to the theme.

---

### Post by dzon65 on 2010-03-12
Let me explain.When I install a firefox theme,where,in which file is it stored.Even with "show hidden files" enabled,I can't find it.

---

### Post by dmillard10 on 2010-03-12
Graphically, you should be able to find like so.

1. Enable hidden files in your home directory.
2. Open the folder '.mozilla'.
3. Open the folder 'firefox'.
4. Open the folder ending in '.default'.
5. Open the folder 'extensions'.
6. As far as I can tell, each theme (along with each addon) has a folder of the form {xxxxxxx}.  Through guess and check, I was able to find what I believe are files relating to my themes.

Hope this helps.

---

### Post by lovinglinux on 2010-03-12
> **dzon65 said:**
> Let me explain.When I install a firefox theme,where,in which file is it stored.Even with "show hidden files" enabled,I can't find it.

Themes are one type of add-ons, so like extensions, they are stored under ~/.mozilla/firefox/extensions.

You will need to know the UID of the theme to locate it. So go to the theme page on Mozilla Add-on site and download it (right-click >> save as) instead of installing it. Then rename the downloaded file from xyz.xpi to xyz.zip. Extract the zipped file somewhere and open the file *install.rdf* with a text editor. Look the for the line like this:

```
<em:id>chromifox@altmusictv.com</em:id>
```

The name between the <em:id> tag is the UID of the theme. This is the name of the folder you should look into the ~/.mozilla/firefox/extensions/ directory.

Keep in mind that if you modify the CSS style of the theme, it will be overwritten when you update the theme with a new version.

So I would recommend creating a new theme, using the one you want to modify as template. You will need to change several things. See [this](https://addons.mozilla.org/en-US/developers/docs/getting-started) for instructions.

Perhaps would be simpler if you use [Stylish](https://addons.mozilla.org/en-US/firefox/addon/2108) extension to modify your theme, so you don't need to create a new one or re-edit every time the theme is updated.

What are you trying to achieve?

---

### Post by dzon65 on 2010-03-12
dmilliard!Thanks,it's been a while since I had to find/use this.It's indeed there.Thanks for that reply.
Kind regards,J

---

### Post by dzon65 on 2010-03-12
[lovinglinux]("http://ubuntuforums.org/member.php?u=649167").Yep,I know,did this before.Only needed the list style image defining the toolbar buttons of that particular style.Thanks for the replies guys!

---

### Post by bluelamp999 on 2010-03-12
> **dzon65 said:**
> ?? I think you misunderstood.Where are they stored.I need the css of an installed theme.

Indeed I did. Apologies...

---

### Post by dzon65 on 2010-03-13
> **lovinglinux said:**
> Themes are one type of add-ons, so like extensions, they are stored under ~/.mozilla/firefox/extensions.

You will need to know the UID of the theme to locate it. So go to the theme page on Mozilla Add-on site and download it (right-click >> save as) instead of installing it. Then rename the downloaded file from xyz.xpi to xyz.zip. Extract the zipped file somewhere and open the file *install.rdf* with a text editor. Look the for the line like this:

```
<em:id>[EMAIL="chromifox@altmusictv.com"]chromifox@altmusictv.com[/EMAIL]</em:id>
```The name between the <em:id> tag is the UID of the theme. This is the name of the folder you should look into the ~/.mozilla/firefox/extensions/ directory.

Keep in mind that if you modify the CSS style of the theme, it will be overwritten when you update the theme with a new version.

So I would recommend creating a new theme, using the one you want to modify as template. You will need to change several things. See [this]("https://addons.mozilla.org/en-US/developers/docs/getting-started") for instructions.

Perhaps would be simpler if you use [Stylish]("https://addons.mozilla.org/en-US/firefox/addon/2108") extension to modify your theme, so you don't need to create a new one or re-edit every time the theme is updated.

What are you trying to achieve?

No worries,Stylish been installed for years.Need the base64 code of the theme to change the FF toolbar buttons.It's that light greyish theme:[http://dzon65.deviantart.com/](http://dzon65.deviantart.com/) So,now it can be done.Totally forgotten where the themes were stored.The aaaaaaaage I guess.
Regards,J.

---

