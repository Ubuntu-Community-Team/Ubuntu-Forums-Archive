---
title: "how do i use clamav (gnome gui clamtk)(kde gui klamav) to scan thunderbird incoming"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-01-10
how do i use clamav (gnome gui clamtk)(kde gui klamav) to scan thunderbird incoming and outgoing mail? Below is all i can find and I have come to you the experts to find out how to do this.
Does anyone know if what is said below will even work?

How do I configure my generic email client to filter mail and catch viruses in incoming email with KlamAV?
    Your email client needs a filter/rule - with the highest priority - to pipe ALL email messages through the klammail program which is installed with KlamAV. This will return the message to the email client with a few new email headers. If a virus is found, this will be noted in the new headers: 
X-Virus-Status: Yes
X-Virus-Checker: Scanned by KlamAV 0.37 on linux (virus-found Eicar-Test-Signature); Mon, 19 Jun 2006 11:57:52 -0400
    Create a second rule, to be run immediately after the first which either deletes or quarantines any mails with the text "virus-found" in the X-Virus-Checker header. 
This technique works with KMail but may not be supported by other email clients, e.g. Novell Evolution 2.8.1.
Note: This technique is for filtering incoming email only. 
(above is from [http://klamav.sourceforge.net/klamavwiki/index.php/FAQ#How_do_I_configure_my_generic_email_client_to_filter_mail_and_catch_viruses_in_incoming_email_with_KlamAV.3F](http://klamav.sourceforge.net/klamavwiki/index.php/FAQ#How_do_I_configure_my_generic_email_client_to_filter_mail_and_catch_viruses_in_incoming_email_with_KlamAV.3F))

---

### Post by virtdave@mcn.org on 2011-02-03
Did you ever get sorted out with this question?  I have the same one.  It's probably simple, but it's not clear to me how to 'pipe' the incoming email through klammail on to Thunderbird.  I can't find KlamAV or klammail  in my applications--I assume the filters are for one of those, not for Thunderbird.

---

### Post by TechWiz2100 on 2011-02-03
[http://ubuntuforums.org/showthread.php?t=885261](http://ubuntuforums.org/showthread.php?t=885261)

Lil' googling goes a long way

---

### Post by virtdave@mcn.org on 2011-02-05
clamdrib, however, is not compatible with Thunderbird 3.1.7.  I found one which is supposed to be ok with 3.1.6, but not with 3.1.7.....and the Thunderbird add-on site does not come up with anything....any further ideas?

---

### Post by virtdave@mcn.org on 2011-02-06
I found the answer to my most recent question  at:   [http://ubuntuforums.org/showthread.php?t=1592433&highlight=panix ]("http://ubuntuforums.org/showthread.php?t=1592433&highlight=panix")
Seems to work....there's a further link there to a downloadable zip file, which when unzipped yields an .xpi file, which Thunderbird 3.1.7 will accept as an add-on.

---

