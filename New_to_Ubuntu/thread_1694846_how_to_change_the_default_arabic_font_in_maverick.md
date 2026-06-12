---
title: "how to change the default arabic font in maverick"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by sheriftaher on 2011-02-24
Hi, I've done some search on the internet and found out that you can change gnome font from System->Preferencesu->Appearance, but it doesn't change the arabic font (and may be other international fonts as well)
I did a lot of search and know how to download and install different fonts from the web, but still couldn't figure out how to use the international fonts

any help is appreciated

thanks

---

### Post by grahammechanical on 2011-02-25
So, you go to System>Preferences>Appearance and you select the fonts tab. Then what? There are panels telling you what font and what size is being used for applications, desktop and other things. Click on the panel and a drop down list of fonts will appear. Choose the one you want. But first the font you want must be in the correct folder for it to be in the list.

There is a way to do this but Ubuntu does not make it easy to find. I have done it. Let me have some time to think and practice.

Regards.

According to the help documentation to install and remove fonts we use the Nautilus file manager program but there is not any information on how to do this. And I cannot work out how to do it. Here is another way that I have used before. Go to Places>Home Folder. Click View and select Show Hidden Files. Look for a file called .fonts. Paste your new fonts into this folder and reboot. These fonts will become available to applications such as word processors. They will also appear in the fonts list of Appearances. It worked for me.

---

### Post by ChipOManiac on 2011-03-15
I had this problem with Urdu fonts before. :D

I fixed it using the [FONT="Courier New"]~/.fonts.conf file[/FONT]. 
1. Fire up the text editor and open [FONT="Courier New"]~/.fonts.conf[/FONT], if it does'nt exist, then make a new file under that name. 
2. Paste the below text (with the relevant parts changed).
3. Save
4. LogOut and back in

Text (Replace ** With Relevant Data):
```

<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
   <match target="pattern">
      <test name="lang" qual="any">
         <string>**</string>
      </test>
      <edit name="family" mode="assign" binding="same">
         <string>**</string>
      </edit>
    </match>
</fontconfig>

```

ISO for arabic is "ar" I think so just replace ** in "lang" with it.

Note: In case the file DID exist just paste from "[FONT="Courier New"]<match...[/FONT]" to "[FONT="Courier New"]</match>[/FONT]"

Hope this helps...

---

