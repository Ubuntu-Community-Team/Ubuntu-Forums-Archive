---
title: "TimeZone Data, Thunderbird, Lightning"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by terribletrouble on 2008-04-15
Not sure if this is the best forum, but issue relates to TimeZone, so I feel related to Networking.

Ubuntu knows eastern time zone as: America/New_York

In reality, it is EDT, EST, Eastern, America/New_York, (etc...?)

When you get a calendar invite to  lightning, from for example Lotus Notes, it looks as follows:(Notes just one example, each one seems a little different...)

```
BEGIN:VCALENDAR
X-LOTUS-CHARSET:UTF-8
VERSION:2.0
PRODID:-//Lotus Development Corporation//NONSGML Notes 8.0//EN
METHOD:REQUEST
BEGIN:VTIMEZONE
TZID:Eastern
BEGIN:STANDARD
DTSTART:19501105T020000
TZOFFSETFROM:-0400
TZOFFSETTO:-0500
RRULE:FREQ=YEARLY;BYMINUTE=0;BYHOUR=2;BYDAY=1SU;BYMONTH=11
END:STANDARD
BEGIN:DAYLIGHT
DTSTART:19500312T020000
TZOFFSETFROM:-0500
TZOFFSETTO:-0400
RRULE:FREQ=YEARLY;BYMINUTE=0;BYHOUR=2;BYDAY=2SU;BYMONTH=3
END:DAYLIGHT
END:VTIMEZONE
BEGIN:VEVENT
DTSTART;TZID="Eastern":20080417T100000
DTEND;TZID="Eastern":20080417T110000
TRANSP:OPAQUE
DTSTAMP:20080407T181503Z

```

It seems Gutsy has no way of interpreting this, and so, in Lightning, you end up with UTC, probably the default fall back.

I would like to assume, the most simple process, is to add the extra names to the tzdata, does anyone know if this will work, or makes sense.

You know what this does to a calendar? You cannot trust it anymore.

---

