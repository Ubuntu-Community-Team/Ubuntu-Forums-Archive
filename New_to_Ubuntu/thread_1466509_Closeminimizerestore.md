---
title: "Close/minimize/restore"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by Mauler5858 on 2010-04-30
Call me a creature of habit, but i cannot get used to these buttons being left.  How can i restore them back to the right like i am used to?

Thanks

---

### Post by bowens44 on 2010-04-30
the easiest way is to just choose a different theme.

---

### Post by philinux on 2010-04-30
The buttons are in the old location on all default themes apart from Ambiance,Radiance and Dust, If you still want the Ambiance ,Radiance or Dust theme but with buttons on the right, choose one of those other themes and use the Customize button to achieve what you want. e.g.
1. System > Preferences > Appearance
2. Select the theme "New Wave"
3. Click Customize
4. Select tab "Controls" and select "Ambiance"
5. Select tab "Window border" and select "Ambiance"
6. Select tab "Icons" and scroll down and select "Ubuntu-mono-dark"
7. Select "Save Theme" to your choice.

---

### Post by Wobblybob on 2010-04-30
go to [preferences], [appearance] and select another theme option or you could install ubuntu-tweak [Google it and follow the instructions to install] it has an option to move the buttons within the current theme [you can even have then in the middle]

---

### Post by Mauler5858 on 2010-04-30
> **philinux said:**
> The buttons are in the old location on all default themes apart from Ambiance,Radiance and Dust, If you still want the Ambiance ,Radiance or Dust theme but with buttons on the right, choose one of those other themes and use the Customize button to achieve what you want. e.g.
1. System > Preferences > Appearance
2. Select the theme "New Wave"
3. Click Customize
4. Select tab "Controls" and select "Ambiance"
5. Select tab "Window border" and select "Ambiance"
6. Select tab "Icons" and scroll down and select "Ubuntu-mono-dark"
7. Select "Save Theme" to your choice.

Thanks, but when i tried...it still forces left aligned buttons.

---

### Post by philinux on 2010-04-30
> **Mauler5858 said:**
> Thanks, but when i tried...it still forces left aligned buttons.

Funny. Just reset mine, by choosing the ambiance theme and then went through my points and it works fine.

---

### Post by dmglouis on 2010-04-30
There is another way, if you want to keep the theme.

Hit Alt-F2
Type in gconf-editor
Browse to apps>metacity>general

In the button layout field, edit the value to be :maximize,minimize,close

wala! Your buttons are now on the right :)

---

### Post by Mauler5858 on 2010-04-30
> **dmglouis said:**
> There is another way, if you want to keep the theme.

Hit Alt-F2
Type in gconf-editor
Browse to apps>metacity>general

In the button layout field, edit the value to be :maximize,minimize,close

wala! Your buttons are now on the right :)

Awesome, worked like a charm!

---

### Post by alvevind on 2010-04-30
Another easy way to restore the window button position is to install the right aligned theme:

Step-by-step procedure:
1. Download the modified theme [http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz](http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz)
2. Open the menu "System" > "Preferences" > "Appearance"
3. Click the button "Install"
4. Open the folder "Downloads"
5. Select the file "Ambience_Radiance-Right.tar.gz"
6. Click "Open"
7. Select the new theme "Ambiance-right"

You then have both the standard unmodified left-aligned theme and the right-aligned theme available and can easily switch back and forth between them with a single click.

---

