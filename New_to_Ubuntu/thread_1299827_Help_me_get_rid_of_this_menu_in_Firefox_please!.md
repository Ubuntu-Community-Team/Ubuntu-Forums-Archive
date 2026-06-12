---
title: "Help me get rid of this menu in Firefox please!"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by Dangger on 2009-10-24
**Solution in further comments. **


Please help me get rid of so many options for spell checking! How can I remove them?

[[IMG]http://imgur.com/8egkes.png[/IMG]](http://imgur.com/8egke.png)

---

### Post by kvarley on 2009-10-24
Remove the addon from firefox and add an addon for the language you require?

Can you edit a config file to only show you certain languages?

---

### Post by Dangger on 2009-10-24
> **vitium said:**
> Remove the addon from firefox and add an addon for the language you require?

Can you edit a config file to only show you certain languages?

I have no add ons for languages except for English and Spanish, look:

[[IMG]http://imgur.com/O6OIhs.png[/IMG]](http://imgur.com/O6OIh.png)

[[IMG]http://imgur.com/afGJ0s.png[/IMG]](http://imgur.com/afGJ0.png)

It's terrible, I have uninstalled every language except for these two in my computer and it still shows every language theoretically available in Ubuntu as an option.

How can I edit the config file to only show two?

Thanks for your help :D

---

### Post by Dangger on 2009-10-24
bump...

---

### Post by arochester on 2009-10-24
How about...

Firefox>Edit>Preferences>Content>Languages>Choose Button> If any language shows that you dont need>Remove Button

Onlu keep what you need.

---

### Post by Dangger on 2009-10-24
> **arochester said:**
> How about...

Firefox>Edit>Preferences>Content>Languages>Choose Button> If any language shows that you dont need>Remove Button

Onlu keep what you need.

No luck, I only have English installed there:

[[IMG]http://imgur.com/eUfB8s.png[/IMG]](http://imgur.com/eUfB8.png)

Thanks for the suggestion though!

---

### Post by Dangger on 2009-10-25
Finally found the problem. I had all the dictionaries available installed and I proceeded to uninstall them in the following way:

First I thought this was related to Open Office and since I have MS Office with crossover I just uninstalled OO by going into Synaptic and removing every entry that had the Openoffice word in it. All of this was removed:

[HTML]hunspell-ar will be removed with configuration
hunspell-de-at will be removed with configuration
hunspell-de-ch will be removed with configuration
hunspell-de-de will be removed with configuration
language-pack-en-base will be removed with configuration
language-pack-es-base will be removed with configuration
language-pack-gnome-en-base will be removed with configuration
language-pack-gnome-es-base will be removed with configuration
language-pack-gnome-ha-base will be removed with configuration
language-pack-gnome-ig-base will be removed with configuration
language-pack-gnome-ks-base will be removed with configuration
language-pack-gnome-mai-base will be removed with configuration
language-pack-gnome-pap-base will be removed with configuration
language-pack-gnome-sa-base will be removed with configuration
language-pack-gnome-shs-base will be removed with configuration
language-pack-gnome-tk-base will be removed with configuration
language-pack-ha-base will be removed with configuration
language-pack-ig-base will be removed with configuration
language-pack-ks-base will be removed with configuration
language-pack-mai-base will be removed with configuration
language-pack-pap-base will be removed with configuration
language-pack-sa-base will be removed with configuration
language-pack-shs-base will be removed with configuration
language-pack-tk-base will be removed with configuration
language-support-translations-es will be removed with configuration
myspell-af will be removed with configuration
myspell-bg will be removed with configuration
myspell-ca will be removed with configuration
myspell-cs-cz will be removed with configuration
myspell-el-gr will be removed with configuration
myspell-en-au will be removed with configuration
myspell-en-gb will be removed with configuration
myspell-en-za will be removed with configuration
myspell-eo will be removed with configuration
myspell-es will be removed with configuration
myspell-et will be removed with configuration
myspell-fa will be removed with configuration
myspell-ga will be removed with configuration
myspell-gd will be removed with configuration
myspell-gv will be removed with configuration
myspell-he will be removed with configuration
myspell-hr will be removed with configuration
myspell-hu will be removed with configuration
myspell-hy will be removed with configuration
myspell-it will be removed with configuration
myspell-ku will be removed with configuration
myspell-lt will be removed with configuration
myspell-lv will be removed with configuration
myspell-nl will be removed with configuration
myspell-nn will be removed with configuration
myspell-pl will be removed with configuration
myspell-pt-br will be removed with configuration
myspell-pt-pt will be removed with configuration
myspell-ru will be removed with configuration
myspell-sk will be removed with configuration
myspell-sl will be removed with configuration
myspell-sv-se will be removed with configuration
myspell-sw will be removed with configuration
myspell-th will be removed with configuration
myspell-uk will be removed with configuration
openoffice.org will be removed with configuration
openoffice.org-base will be removed with configuration
openoffice.org-calc will be removed with configuration
openoffice.org-draw will be removed with configuration
openoffice.org-emailmerge will be removed with configuration
openoffice.org-filter-binfilter will be removed with configuration
openoffice.org-filter-mobiledev will be removed with configuration
openoffice.org-gnome will be removed with configuration
openoffice.org-gtk will be removed with configuration
openoffice.org-help-en-gb will be removed with configuration
openoffice.org-help-en-us will be removed with configuration
openoffice.org-help-es will be removed with configuration
openoffice.org-help-fr will be removed with configuration
openoffice.org-help-pt will be removed with configuration
openoffice.org-help-pt-br will be removed with configuration
openoffice.org-hyphenation will be removed with configuration
openoffice.org-hyphenation-en-us will be removed with configuration
openoffice.org-impress will be removed with configuration
openoffice.org-java-common will be removed with configuration
openoffice.org-l10n-common will be removed with configuration
openoffice.org-l10n-en-gb will be removed with configuration
openoffice.org-l10n-en-za will be removed with configuration
openoffice.org-l10n-es will be removed with configuration
openoffice.org-l10n-fr will be removed with configuration
openoffice.org-l10n-pt will be removed with configuration
openoffice.org-l10n-pt-br will be removed with configuration
openoffice.org-math will be removed with configuration
openoffice.org-officebean will be removed with configuration
openoffice.org-report-builder-bin will be removed with configuration
openoffice.org-style-human will be removed with configuration
openoffice.org-thesaurus-en-au will be removed with configuration
openoffice.org-thesaurus-en-us will be removed with configuration
openoffice.org-writer will be removed with configuration
python-uno will be removed with configuration
ttf-opensymbol will be removed with configuration
uno-libs3 will be removed with configuration
ure will be removed with configuration
couchdb-bin will be removed
desktopcouch will be removed
empathy will be removed
evolution will be removed
evolution-couchdb will be removed
evolution-documentation-cs will be removed
evolution-documentation-de will be removed
evolution-documentation-el will be removed
evolution-documentation-es will be removed
evolution-documentation-fr will be removed
evolution-documentation-mk will be removed
evolution-documentation-oc will be removed
evolution-documentation-ru will be removed
evolution-documentation-sv will be removed
evolution-exchange will be removed
evolution-indicator will be removed
evolution-plugins will be removed
gedit will be removed
gnome-user-guide will be removed
gnome-user-guide-en will be removed
gnome-user-guide-es will be removed
language-pack-en will be removed
language-pack-es will be removed
language-pack-gnome-en will be removed
language-pack-gnome-es will be removed
language-pack-gnome-ha will be removed
language-pack-gnome-ig will be removed
language-pack-gnome-ks will be removed
language-pack-gnome-mai will be removed
language-pack-gnome-pap will be removed
language-pack-gnome-sa will be removed
language-pack-gnome-shs will be removed
language-pack-gnome-tk will be removed
language-pack-ha will be removed
language-pack-ig will be removed
language-pack-ks will be removed
language-pack-mai will be removed
language-pack-pap will be removed
language-pack-sa will be removed
language-pack-shs will be removed
language-pack-tk will be removed
language-support-translations-en will be removed
language-support-writing-en will be removed
language-support-writing-es will be removed
libempathy-gtk28 will be removed
libenchant-voikko will be removed
libenchant1c2a will be removed
libgtkhtml-editor0 will be removed
libgtkhtml3.14-19 will be removed
libgtkspell0 will be removed
libsexy2 will be removed
libwebkit-1.0-2 will be removed
myspell-pt will be removed
notification-daemon will be removed
openoffice.org-base-core will be removed
openoffice.org-core will be removed
pidgin will be removed
pidgin-libnotify will be removed
pidgin-otr will be removed
policykit-gnome will be removed
python-desktopcouch will be removed
python-desktopcouch-records will be removed
python-sexy will be removed
python-webkit will be removed
software-center will be removed
sun-java6-plugin will be removed
thunderbird-locale-en-gb will be removed
thunderbird-locale-es-ar will be removed
thunderbird-locale-es-es will be removed
tomboy will be removed
ubuntu-desktop will be removed
ubuntu-docs will be removed
ubuntu-tweak will be removed
xulrunner-1.9 will be removed
xulrunner-1.9-gnome-support will be removed[/HTML]

When I restarted FF almost all of the languages were gone but some remained (this also removed Ubuntu tweak, Software Center, Gedit and many other applications that I haven't reinstalled). Then I noticed that it had to do with all the dictionary packages that were installed by "default" (I have a customized ubuntu dvd provided by Dell). So I went hunting for all except the ones I needed. 

First searched for myspell and removed:

[HTML]myspell-fo will be removed with configuration
myspell-nb will be removed with configuration
myspell-nr will be removed with configuration
myspell-ns will be removed with configuration
myspell-ro will be removed with configuration
myspell-ss will be removed with configuration
myspell-st will be removed with configuration
myspell-tn will be removed with configuration
myspell-ts will be removed with configuration
myspell-ve will be removed with configuration
myspell-xh will be removed with configuration
myspell-zu will be removed with configuration[/HTML]

Then ispell and aspell:

[HTML]aspell-tl will be removed with configuration
tmispell-voikko will be removed with configuration
wdutch will be removed with configuration[/HTML]

Then dictionary:

[HTML]hunspell-da will be removed with configuration
hunspell-eu-es will be removed with configuration
hunspell-ne will be removed with configuration
hunspell-uz will be removed with configuration
wbulgarian will be removed with configuration
wcatalan will be removed with configuration
wdanish will be removed with configuration
wfaroese will be removed with configuration
wirish will be removed with configuration
witalian will be removed with configuration
wmanx will be removed with configuration
wngerman will be removed with configuration
wogerman will be removed with configuration
wpolish will be removed with configuration
wswedish will be removed with configuration
wswiss will be removed with configuration
wukrainian will be removed with configuration[/HTML]

Then hunspell:

[HTML]hunspell-en-us will be removed with configuration
hunspell-fr will be removed with configuration
hunspell-se will be removed with configuration[/HTML]


So anyways, you don't need to remove Open Office or all the other programs, just get rid of the dictionaries.

---

