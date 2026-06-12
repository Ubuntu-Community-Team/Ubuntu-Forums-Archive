---
title: "Spamassassin --lint shows missining Plugins. Where are they?"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by hulmgulm on 2007-08-17
I just installed Ubunutu 7.04 on my server and I'm in the process to configure all the needed applications.  However spamassassin does complain about some missing plugins:


> [28081] warn: plugin: failed to parse plugin (from @INC): Can't locate Mail/SpamAssassin/Plugin/Check.pm in @INC (@INC contains: lib /usr/share/perl5 /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl) at (eval 76) line 1.
[28081] warn: plugin: failed to create instance of plugin Mail::SpamAssassin::Plugin::Check: Can't locate object method "new" via package "Mail::SpamAssassin::Plugin::Check" at (eval 77) line 1.
[28081] warn: plugin: failed to parse plugin (from @INC): Can't locate Mail/SpamAssassin/Plugin/HTTPSMismatch.pm in @INC (@INC contains: lib /usr/share/perl5 /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl) at (eval 78) line 1.
[28081] warn: plugin: failed to create instance of plugin Mail::SpamAssassin::Plugin::HTTPSMismatch: Can't locate object method "new" via package "Mail::SpamAssassin::Plugin::HTTPSMismatch" at (eval 79) line 1.
[28081] warn: plugin: failed to parse plugin (from @INC): Can't locate Mail/SpamAssassin/Plugin/URIDetail.pm in @INC (@INC contains: lib /usr/share/perl5 /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl) at (eval 80) line 1.
[28081] warn: plugin: failed to create instance of plugin Mail::SpamAssassin::Plugin::URIDetail: Can't locate object method "new" via package "Mail::SpamAssassin::Plugin::URIDetail" at (eval 81) line 1.
[28081] warn: plugin: failed to parse plugin (from @INC): Can't locate Mail/SpamAssassin/Plugin/Bayes.pm in @INC (@INC contains: lib /usr/share/perl5 /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl) at (eval 82) line 1.
[28081] warn: plugin: failed to create instance of plugin Mail::SpamAssassin::Plugin::Bayes: Can't locate object method "new" via package "Mail::SpamAssassin::Plugin::Bayes" at (eval 83) line 1.
[28081] warn: plugin: failed to parse plugin (from @INC): Can't locate Mail/SpamAssassin/Plugin/BodyEval.pm in @INC (@INC contains: lib /usr/share/perl5 /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl) at (eval 84) line 1.
[28081] warn: plugin: failed to create instance of plugin Mail::SpamAssassin::Plugin::BodyEval: Can't locate object method "new" via package "Mail::SpamAssassin::Plugin::BodyEval" at (eval 85) line 1.
[28081] warn: plugin: failed to parse plugin (from @INC): Can't locate Mail/SpamAssassin/Plugin/DNSEval.pm in @INC (@INC contains: lib /usr/share/perl5 /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl) at (eval 86) line 1.
[28081] warn: plugin: failed to create instance of plugin Mail::SpamAssassin::Plugin::DNSEval: Can't locate object method "new" via package "Mail::SpamAssassin::Plugin::DNSEval" at (eval 87) line 1.
[28081] warn: plugin: failed to parse plugin (from @INC): Can't locate Mail/SpamAssassin/Plugin/HTMLEval.pm in @INC (@INC contains: lib /usr/share/perl5 /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl) at (eval 88) line 1.
[28081] warn: plugin: failed to create instance of plugin Mail::SpamAssassin::Plugin::HTMLEval: Can't locate object method "new" via package "Mail::SpamAssassin::Plugin::HTMLEval" at (eval 89) line 1.
[28081] warn: plugin: failed to parse plugin (from @INC): Can't locate Mail/SpamAssassin/Plugin/HeaderEval.pm in @INC (@INC contains: lib /usr/share/perl5 /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl) at (eval 90) line 1.
[28081] warn: plugin: failed to create instance of plugin Mail::SpamAssassin::Plugin::HeaderEval: Can't locate object method "new" via package "Mail::SpamAssassin::Plugin::HeaderEval" at (eval 91) line 1.
[28081] warn: plugin: failed to parse plugin (from @INC): Can't locate Mail/SpamAssassin/Plugin/MIMEEval.pm in @INC (@INC contains: lib /usr/share/perl5 /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl) at (eval 92) line 1.
[28081] warn: plugin: failed to create instance of plugin Mail::SpamAssassin::Plugin::MIMEEval: Can't locate object method "new" via package "Mail::SpamAssassin::Plugin::MIMEEval" at (eval 93) line 1.
[28081] warn: plugin: failed to parse plugin (from @INC): Can't locate Mail/SpamAssassin/Plugin/RelayEval.pm in @INC (@INC contains: lib /usr/share/perl5 /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl) at (eval 94) line 1.
[28081] warn: plugin: failed to create instance of plugin Mail::SpamAssassin::Plugin::RelayEval: Can't locate object method "new" via package "Mail::SpamAssassin::Plugin::RelayEval" at (eval 95) line 1.
[28081] warn: plugin: failed to parse plugin (from @INC): Can't locate Mail/SpamAssassin/Plugin/URIEval.pm in @INC (@INC contains: lib /usr/share/perl5 /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl) at (eval 96) line 1.
[28081] warn: plugin: failed to create instance of plugin Mail::SpamAssassin::Plugin::URIEval: Can't locate object method "new" via package "Mail::SpamAssassin::Plugin::URIEval" at (eval 97) line 1.
[28081] warn: plugin: failed to parse plugin (from @INC): Can't locate Mail/SpamAssassin/Plugin/WLBLEval.pm in @INC (@INC contains: lib /usr/share/perl5 /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl) at (eval 98) line 1.
[28081] warn: plugin: failed to create instance of plugin Mail::SpamAssassin::Plugin::WLBLEval: Can't locate object method "new" via package "Mail::SpamAssassin::Plugin::WLBLEval" at (eval 99) line 1.
[28081] warn: plugin: failed to parse plugin (from @INC): Can't locate Mail/SpamAssassin/Plugin/VBounce.pm in @INC (@INC contains: lib /usr/share/perl5 /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl) at (eval 100) line 1.
[28081] warn: plugin: failed to create instance of plugin Mail::SpamAssassin::Plugin::VBounce: Can't locate object method "new" via package "Mail::SpamAssassin::Plugin::VBounce" at (eval 101) line 1.
[28081] warn: plugin: failed to parse plugin (from @INC): Can't locate Mail/SpamAssassin/Plugin/ImageInfo.pm in @INC (@INC contains: lib /usr/share/perl5 /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl) at (eval 102) line 1.
[28081] warn: plugin: failed to create instance of plugin Mail::SpamAssassin::Plugin::ImageInfo: Can't locate object method "new" via package "Mail::SpamAssassin::Plugin::ImageInfo" at (eval 103) line 1.


Where do I get them? Why aren't they part of the spamassassin deb package?

Thanks for your answers!!!

---

