---
title: "Metacity Themes"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by AlistairH on 2009-09-13
What am I missing?

I've installed a whole load of themes from the repositories via Synaptic Package Manager which put them into the /usr/share/themes directory.

I presumed I'd simply be able to use them by selecting them via the Appearance Preferences dialog, but no. They're not there.

I copied the folders from the /usr/share/themes directory to the .themes directory but still no sign of them in the Appearance Preferences dialog.

What am I doing wrong?

---

### Post by ankspo71 on 2009-09-13
Hi,
I might be wrong... but I can only get metacity themes to work only if the archive contains a index.theme file. I think the themes require those to make them work when you drag and drop them into the theme manager. So gnome might require them if you extract them into /home/<user>/.themes or /user/share/themes too. 

I think gtk themes require a gtkrc file.
I think panels backrounds require a panelrc file.

---

### Post by ankspo71 on 2009-09-13
Hi again,

Are you extracting the themes first?

Btw, some of the themes at gnome-look get downloaded as the wrong archive too. In that case, you might have to rename the file extension, or extract the files then re-archive them into a tar.gz archive. I think tar.bz2 is acceptable too, I'm not sure.

James

EDIT, I goofed up, I missed the part where you said you downloaded them through Synaptic Package Manager. In that case, they should have worked without you having to move them into /user/share/themes, or home/ .themes.

Do you have an example of which theme(s) didn't work?

---

### Post by AlistairH on 2009-09-13
It's sorted. I misunderstood what the themes were doing. I assumed that they would be listed in the theme tab of the Appearance Preferences dialog. In actual fact, I can access them, or their individual element parts at any rate, via the 'customize' button.

Thanks for responding.

---

