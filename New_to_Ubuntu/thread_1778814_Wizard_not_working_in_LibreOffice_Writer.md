---
title: "Wizard not working in LibreOffice Writer"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by geoff_sct on 2011-06-09
I want to use the letter wizard in LibreOffice Writer but it won't come up. I go File > Wizards > Letter and nothing happens. I had tried before and got a message that I needed to install Java Runtime so I installed Open JDK Java Run. Still nothing. Any suggestions?

---

### Post by ajgreeny on 2011-06-09
I have never even tried it before, but in view of your post, have just done so using OpenOffice.org in 10.04, with sun-java, not openjre/jdk, but still got nothing.

I then noticed that I did not have **openoffice-java-common** installed, added that and, Bingo, it now works, so I think you need** libreoffice-java-common** for it to work in that.

---

### Post by geoff_sct on 2011-06-09
Ok I downloaded the add-ons for LibreOffice and now everything works. Thanks.

---

### Post by foolishchild on 2012-01-16
I had same problem, not sure what
"Ok I downloaded the add-ons for LibreOffice and now everything works." 
means, specific fix for me was 
"sudo aptitude install libreoffice-java-common".

---

### Post by paapu on 2012-01-29
Thank's! "sudo aptitude install libreoffice-java-common" solved my problem too. This type of things are very annoying in Linux. One should have some message from Libre Office saying that one should install libreoffice-java-common. Beginners get stuck and switch back to Windows.

---

### Post by layolayo on 2012-04-24
Thank you! I second this @geoff_sct, as much as I love Ubuntu these are some of the small but necessary fixes to aid in the user experiences that can make or break a lasting relationship with Ubuntu. Those not in the nerd-o-sphere do not have the time or inclination to go searching and just presume that things do not work.

Another user issue I also had was the right-click 'Create New Document' - No Templates Installed . Any previous windows user expects to see a list of word/excel/powerpoint etc doc's listed there... Ok, once you understand how it operates all is ok. But without searching and reading bug-reports, once considers the system to be faulty.

[If you want document types to appear there: open a blank writer doc and save as writer.odt in your /Templates folder, do the same for other LibreOffice docs, naming appropriately]

Layolayo

---

