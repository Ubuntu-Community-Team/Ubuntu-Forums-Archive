---
title: "How can I edit items in the Indicator Bar"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by jfloydb on 2010-05-01
I hope that I have my terminology correct, or close enough to convey my question. When I right-click the right-hand side of the upper panel, and click About, I am told about the "Indicator Applet", so I'm assuming that the right-hand side of the upper panel is an "indicator bar"...   

At any rate, here is my question: how can I edit what is displayed in the indicator bar? Specifically: how can I remove the envelope icon and the dialog-bubble icon from the indicator bar? Using 10.04. Thanks.

---

### Post by david20063 on 2010-05-02
Just right click on anything that you want to get rid of and a menu will appear and just click "Remove From Panel" But I will warn you some of these items are grouped together and it may remove more then what you want it to. You may also right click an empty space and click "Add to Panel" and add whatever you want to it.

---

### Post by GSF1200S on 2010-05-02
Are you using Ubuntu Netbook Remix? Unfortunately, in order to remove panel items you need to remove lines from the .xml file located at:
> /var/lib/gconf/une.mandatory/%gconf-tree.xml

---

### Post by jfloydb on 2010-05-02
No, I'm not using the remix. I did right click the dialog balloon icon and removed it. Unfortunately it was connected to my user name and it was removed from the panel as well, but I can live with that. The envelope icon is a different matter: it's connected to the sound/volume icon, which I want to keep, so I'm stuck with the envelope. I now know that these items are applets, and I'll keep what is useful. Thanks for the advice.

Edit: Sorry about the garble in my question. Thanks for your replies, they were helpful. After playing around a bit, I now have my panel items the way that I want them. Thanks again.

---

