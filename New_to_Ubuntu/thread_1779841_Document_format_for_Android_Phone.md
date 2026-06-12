---
title: "Document format for Android Phone?"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by nosehat on 2011-06-11
I have an Android 2.2 phone from Verizon, which has Quickoffice pre-installed.  I would like to be able to use (read and edit) biggish text documents (about 150K of plain text), and sync them with my Ubuntu 10.04 machine.  

Quickoffice supposedly has the ability to read MS Word .doc and .docx files, but no matter how I save my file in Open Office (there are 3 different .doc options, and one for .docx), Quickoffice can't open the file on my Android.  :mad:

The problem could be Quickoffice being fussy about how it expects the .doc files to be formatted.  Maybe Open Office doesn't save a .doc file *exactly* the same way as MS Office?

Or the problem could be the way I'm syncing or copying my files to the Android.  I've noticed that new directories I make on the phone's SD card when it's mounted on my computer will go missing when the phone tries to find them by itself. Files I copy to the phone will sometimes go missing too, reappearing as numbered blocks in the phone's LOST.DIR.  So maybe the problem isn't with Quickoffice at all, but rather with the way I'm mounting the phone and copying the files??  (I just allow the phone to automatically mount through the USB cable, and I use [Unison]("http://www.ubuntugeek.com/unison-file-synchronization-tool.html") to sync the phone's SD card with a mirror directory on my desktop).

So what I'm looking for is some understanding of what the problem might be.  

I'm also looking for any practical solution for quickly loading, reading, and editing largish text files on the Droid that is Ubuntu friendly.  I'm not wedded to Quickoffice, or .doc, or .docx, or .odt -- I'll try any software or file format that lets me get the job done.

Are there any Ubuntu and Android users who work with text and can point me in the right direction??

Thanks in advance!

---

### Post by lavinog on 2011-06-11
Are you unmounting the phone (press the eject icon) before disconnecting it?

---

### Post by nosehat on 2011-06-11
@lavinog:

I am right-clicking on the Motorola icon on my desktop, and selecting "Safely Remove Drive"

Two separate things mount in /media when I plug the phone in:  "Motorola" and "8GB File System".  "Motorola" looks like a CD and just has a "setup.exe" and a couple other files on it. The "8GB File System" is the SD card, and that what I'm syncing and copying to.  When I "Safely Remove Drive" to the one labeled "Motorola", they both unmount.

---

### Post by nosehat on 2011-06-11
I should add, I'm doing nothing at all with the phone itself during this process except plugging it in at the start, and unplugging it after unmounting the drives.

---

### Post by sanderd17 on 2011-06-11
Just for the case that the mounting is the problem. Android detects a computer and automatically unmounts its own sd card and shows it to a computer (this is not true in all versions, but it seems to be so in yours). So unmounting from a computer does not mount it to your android device, the sd card is still available for the computer. You should unplug the usb cable.

btw, if it's plain text, why don't you use a plain text editor?

---

### Post by nosehat on 2011-06-11
I think the occasional mounting/file system issues might be a bit of a red herring.  Aside from the disappearing directories and the occasional lost file, most file transfers work just fine using my method.  I've copied hundreds of photos, mp3s, epub books, text files, etc back and forth without incident.

> **sanderd17 said:**
> btw, if it's plain text, why don't you use a plain text editor?

Sorry, I should have been more clear.  I said 150K of plain text to give an indication of how large the files are.  A doc or docx or odt of this text could be any size between less than 100K to over 300K.  The files in their "native" format on my computer are .odt files.  There is no .odt file editor yet developed for Android, although there are a couple of readers.

I greatly prefer to use a format that allows for some text formatting, since that makes the information much easier to work with.  I've got a text file editor, called TED, on my phone, but it's slow and clunky for big files.  In fact, quickoffice is also slow and clunky for big files.

I was hoping someone else might be in the same boat as me, and found a workaround that can force open office to save a file in a format the quickoffice can open 100% of the time.  Or someone's found a different android app/file format combination that works better than quickoffice.

---

### Post by sanderd17 on 2011-06-11
And what do you think about Gdocs?

you need to upload your files to Google docs, you can see them in formatted layout in the docs app and you can edit the plain text (so no markup editing) in another app called Gdocs. 

You do need an internet connection.

is this sufficient for you?

---

### Post by nosehat on 2011-06-11
Thanks, sanderd17, that's a good suggestion.  I see that Google has its own app to interface with Google docs as well.

However, I'm really looking for an off-line and off-the-cloud solution for my documents.  I've already got a way to sync my phone with my desktop, so I don't need the cloud for that.  

I'm just looking for a mutually compatible document format that will let me use open office on my computer, and anything else on the Droid.

---

