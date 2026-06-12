---
title: "No Audio in New Amarok."
date: 2009-05-16
forum: New to Ubuntu
---

### Post by osc1882 on 2009-05-16
Other then the fact that I don't know if i like the new lay out of Amarok (maybe I'll change my mind later, lol.) I can't get it to play any audio.

So I ran it using the terminal and copy and pasted all of the bugs it gave me while the program booted. I was wondering if anyone could decipher any of this.  





grammatrain@tprb:~$ amarok %U
amarok(4327) Phonon::KdePlatformPlugin::createBackend: using backend:  "GStreamer"
Object::connect: No such slot MainWindow::showStatistics() in /build/buildd/amarok-2.0.2mysql5.1.30/amarok-2.0.2/src/MainWindow.cpp:692
Object::connect:  (receiver name: 'MainWindow')
QLayout: Attempting to add QLayout "" to MainWindow "MainWindow", which already has a layout
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
amarok(4327) Plasma::Applet::save: saving to "1"
amarok(4327) Context::ContextView::setContainment: "" Line:  599
amarok(4327) Plasma::ThemePrivate::config: using theme for app "amarok"
amarok(4327) Plasma::Applet::save: saving to "2"

---

### Post by lhb1142 on 2009-05-16
FWIW: I very much liked Amarok 1.4 but I do not like the new Amarok2 at all. I have abandoned it (as well as Songbird) in favor of Audacious. In addition, I am using Streamtuner, which coordinates with Audacious, so now, not only can I LISTEN to a lot of internet radio stations, I can also RECORD them. (Tunapie does the same thing but I prefer Streamtuner.)

Also I have no trouble listening to my archived music with Audacious.

I recommend that you try it - you get it from the Synaptic Package Manager, You can also find Streamtuner there. If you're not happy with these two, you can always remove them and continue to experiment with Amarok2. (If you do choose to keep Amarok2, make sure you go into Synatptic Package Manager, search for Amarok, and install every codec and option available for it.)  ):P

---

