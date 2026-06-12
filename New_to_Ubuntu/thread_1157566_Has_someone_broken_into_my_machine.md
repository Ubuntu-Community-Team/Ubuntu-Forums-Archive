---
title: "Has someone broken into my machine?"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by AncientPC on 2009-05-12
I have an open ssh port to the public and it gets regularly attacked.  I don't worry about it too much since I only have one account with ssh access with a large keyspace (10+ password length combination of letter, number, symbols, and casing).

However today I noticed my internet was crawling to a lag and after checking my router's admin page I noticed that my entire outbound bandwith was saturated from port 22 to a Poland IP.  The connection was confirmed via netstat.

Grepping auth.log gives me below:
```
May 12 18:00:30 punk sshd[12687]: Did not receive identification string from 194.29.180.1
May 12 18:04:51 punk sshd[12690]: Failed password for root from 194.29.180.1 port 51603 ssh2
May 12 18:04:55 punk sshd[12694]: Failed password for root from 194.29.180.1 port 52779 ssh2
May 12 18:04:59 punk sshd[12696]: Failed password for root from 194.29.180.1 port 53027 ssh2
May 12 18:05:03 punk sshd[12700]: Failed password for root from 194.29.180.1 port 53694 ssh2
May 12 18:05:07 punk sshd[12702]: Failed password for root from 194.29.180.1 port 54343 ssh2
May 12 18:05:11 punk sshd[12706]: Failed password for root from 194.29.180.1 port 54999 ssh2
May 12 18:05:14 punk sshd[12708]: Failed password for root from 194.29.180.1 port 55285 ssh2
May 12 18:05:18 punk sshd[12712]: Failed password for root from 194.29.180.1 port 55935 ssh2
May 12 18:05:22 punk sshd[12714]: Failed password for root from 194.29.180.1 port 56571 ssh2
May 12 18:05:26 punk sshd[12716]: Failed password for root from 194.29.180.1 port 57238 ssh2
May 12 18:05:29 punk sshd[12733]: Failed password for root from 194.29.180.1 port 41714 ssh2
May 12 18:05:33 punk sshd[12735]: Failed password for root from 194.29.180.1 port 41931 ssh2
May 12 18:05:37 punk sshd[12739]: Failed password for root from 194.29.180.1 port 42585 ssh2
May 12 18:05:41 punk sshd[12741]: Failed password for root from 194.29.180.1 port 44888 ssh2
May 12 18:05:45 punk sshd[12745]: Failed password for root from 194.29.180.1 port 45606 ssh2
May 12 18:05:49 punk sshd[12747]: Failed password for root from 194.29.180.1 port 46098 ssh2
May 12 18:05:53 punk sshd[12750]: Failed password for root from 194.29.180.1 port 46744 ssh2
May 12 18:05:57 punk sshd[12753]: Failed password for root from 194.29.180.1 port 47414 ssh2
May 12 18:06:01 punk sshd[12755]: Failed password for root from 194.29.180.1 port 47888 ssh2
May 12 18:06:05 punk sshd[12759]: Failed password for root from 194.29.180.1 port 48439 ssh2
May 12 18:06:09 punk sshd[12761]: Failed password for root from 194.29.180.1 port 49240 ssh2
May 12 18:06:12 punk sshd[12765]: Failed password for root from 194.29.180.1 port 49930 ssh2
May 12 18:06:16 punk sshd[12767]: Failed password for root from 194.29.180.1 port 50707 ssh2
May 12 18:06:20 punk sshd[12771]: Failed password for root from 194.29.180.1 port 51296 ssh2
May 12 18:06:24 punk sshd[12775]: Failed password for root from 194.29.180.1 port 51785 ssh2
May 12 18:06:28 punk sshd[12778]: Failed password for root from 194.29.180.1 port 52423 ssh2
May 12 18:06:32 punk sshd[12781]: Failed password for root from 194.29.180.1 port 53107 ssh2
May 12 18:06:35 punk sshd[12783]: Failed password for root from 194.29.180.1 port 53584 ssh2
May 12 18:06:39 punk sshd[12787]: Failed password for root from 194.29.180.1 port 54075 ssh2
May 12 18:06:43 punk sshd[12789]: Failed password for root from 194.29.180.1 port 54750 ssh2
May 12 18:06:47 punk sshd[12793]: Failed password for root from 194.29.180.1 port 55398 ssh2
May 12 18:06:51 punk sshd[12795]: Failed password for root from 194.29.180.1 port 56079 ssh2
May 12 18:06:55 punk sshd[12799]: Failed password for root from 194.29.180.1 port 56378 ssh2
May 12 18:06:59 punk sshd[12801]: Failed password for root from 194.29.180.1 port 57030 ssh2
May 12 18:07:00 punk sshd[12803]: Invalid user administrator from 194.29.180.1
May 12 18:07:02 punk sshd[12803]: Failed password for invalid user administrator from 194.29.180.1 port 57737 ssh2
May 12 18:07:04 punk sshd[12807]: Invalid user administrator from 194.29.180.1
May 12 18:07:05 punk sshd[12807]: Failed password for invalid user administrator from 194.29.180.1 port 58429 ssh2
May 12 18:07:07 punk sshd[12809]: Invalid user administrator from 194.29.180.1
May 12 18:07:09 punk sshd[12809]: Failed password for invalid user administrator from 194.29.180.1 port 58637 ssh2
May 12 18:07:10 punk sshd[12812]: Invalid user administrator from 194.29.180.1
May 12 18:07:12 punk sshd[12812]: Failed password for invalid user administrator from 194.29.180.1 port 59305 ssh2
May 12 18:07:18 punk sshd[12815]: Invalid user administrator from 194.29.180.1
May 12 18:07:21 punk sshd[12815]: Failed password for invalid user administrator from 194.29.180.1 port 59998 ssh2
May 12 18:07:22 punk sshd[12819]: Invalid user administrator from 194.29.180.1
May 12 18:07:24 punk sshd[12819]: Failed password for invalid user administrator from 194.29.180.1 port 60619 ssh2
May 12 18:07:26 punk sshd[12821]: Invalid user administrator from 194.29.180.1
May 12 18:07:28 punk sshd[12821]: Failed password for invalid user administrator from 194.29.180.1 port 32901 ssh2
May 12 18:07:29 punk sshd[12825]: Invalid user administrator from 194.29.180.1
May 12 18:07:32 punk sshd[12825]: Failed password for invalid user administrator from 194.29.180.1 port 33409 ssh2
May 12 18:07:33 punk sshd[12827]: Invalid user administrator from 194.29.180.1
May 12 18:07:35 punk sshd[12827]: Failed password for invalid user administrator from 194.29.180.1 port 33762 ssh2
May 12 18:07:37 punk sshd[12831]: Invalid user administrator from 194.29.180.1
May 12 18:07:39 punk sshd[12831]: Failed password for invalid user administrator from 194.29.180.1 port 34142 ssh2
May 12 18:07:41 punk sshd[12833]: Invalid user administrator from 194.29.180.1
May 12 18:07:43 punk sshd[12833]: Failed password for invalid user administrator from 194.29.180.1 port 34689 ssh2
May 12 18:07:45 punk sshd[12835]: Invalid user administrator from 194.29.180.1
May 12 18:07:48 punk sshd[12835]: Failed password for invalid user administrator from 194.29.180.1 port 35243 ssh2
May 12 18:07:49 punk sshd[12839]: Invalid user postfix from 194.29.180.1
May 12 18:07:51 punk sshd[12839]: Failed password for invalid user postfix from 194.29.180.1 port 35825 ssh2
May 12 18:07:53 punk sshd[12841]: Invalid user postfix from 194.29.180.1
May 12 18:07:55 punk sshd[12841]: Failed password for invalid user postfix from 194.29.180.1 port 36162 ssh2
May 12 18:07:57 punk sshd[12845]: Invalid user postfix from 194.29.180.1
May 12 18:07:59 punk sshd[12845]: Failed password for invalid user postfix from 194.29.180.1 port 36539 ssh2
May 12 18:08:01 punk sshd[12847]: Invalid user postfix from 194.29.180.1
May 12 18:08:02 punk sshd[12847]: Failed password for invalid user postfix from 194.29.180.1 port 37105 ssh2
May 12 18:08:04 punk sshd[12851]: Invalid user postfix from 194.29.180.1
May 12 18:08:06 punk sshd[12851]: Failed password for invalid user postfix from 194.29.180.1 port 37606 ssh2
May 12 18:08:08 punk sshd[12853]: Invalid user postfix from 194.29.180.1
May 12 18:08:10 punk sshd[12853]: Failed password for invalid user postfix from 194.29.180.1 port 37939 ssh2
May 12 18:08:11 punk sshd[12855]: Invalid user postfix from 194.29.180.1
May 12 18:08:13 punk sshd[12855]: Failed password for invalid user postfix from 194.29.180.1 port 38314 ssh2
May 12 18:08:14 punk sshd[12859]: Invalid user postfix from 194.29.180.1
May 12 18:08:16 punk sshd[12859]: Failed password for invalid user postfix from 194.29.180.1 port 38817 ssh2
May 12 18:08:17 punk sshd[12861]: Invalid user postfix from 194.29.180.1
May 12 18:08:19 punk sshd[12861]: Failed password for invalid user postfix from 194.29.180.1 port 38986 ssh2
May 12 18:08:21 punk sshd[12865]: Invalid user test from 194.29.180.1
May 12 18:08:23 punk sshd[12865]: Failed password for invalid user test from 194.29.180.1 port 39518 ssh2
May 12 18:08:24 punk sshd[12867]: Invalid user test from 194.29.180.1
May 12 18:08:26 punk sshd[12867]: Failed password for invalid user test from 194.29.180.1 port 40024 ssh2
May 12 18:08:28 punk sshd[12869]: Invalid user test from 194.29.180.1
May 12 18:08:30 punk sshd[12869]: Failed password for invalid user test from 194.29.180.1 port 40349 ssh2
May 12 18:08:31 punk sshd[12873]: Invalid user test from 194.29.180.1
May 12 18:08:34 punk sshd[12873]: Failed password for invalid user test from 194.29.180.1 port 40718 ssh2
May 12 18:08:35 punk sshd[12875]: Invalid user test from 194.29.180.1
May 12 18:08:37 punk sshd[12875]: Failed password for invalid user test from 194.29.180.1 port 41246 ssh2
May 12 18:08:38 punk sshd[12879]: Invalid user test from 194.29.180.1
May 12 18:08:41 punk sshd[12879]: Failed password for invalid user test from 194.29.180.1 port 41617 ssh2
May 12 18:08:43 punk sshd[12881]: Invalid user test from 194.29.180.1
May 12 18:08:45 punk sshd[12881]: Failed password for invalid user test from 194.29.180.1 port 42230 ssh2
May 12 18:08:46 punk sshd[12885]: Invalid user test from 194.29.180.1
May 12 18:08:48 punk sshd[12885]: Failed password for invalid user test from 194.29.180.1 port 42619 ssh2
May 12 18:08:49 punk sshd[12887]: Invalid user test from 194.29.180.1
May 12 18:08:51 punk sshd[12887]: Failed password for invalid user test from 194.29.180.1 port 43051 ssh2
May 12 18:08:52 punk sshd[12889]: Invalid user test from 194.29.180.1
May 12 18:08:54 punk sshd[12889]: Failed password for invalid user test from 194.29.180.1 port 43306 ssh2
May 12 18:08:56 punk sshd[12893]: Invalid user test from 194.29.180.1
May 12 18:08:58 punk sshd[12893]: Failed password for invalid user test from 194.29.180.1 port 43770 ssh2
May 12 18:08:59 punk sshd[12895]: Invalid user test from 194.29.180.1
May 12 18:09:01 punk sshd[12895]: Failed password for invalid user test from 194.29.180.1 port 44233 ssh2
May 12 18:09:03 punk sshd[12897]: Invalid user test from 194.29.180.1
May 12 18:09:05 punk sshd[12897]: Failed password for invalid user test from 194.29.180.1 port 44610 ssh2
May 12 18:09:07 punk sshd[12901]: Invalid user test from 194.29.180.1
May 12 18:09:08 punk sshd[12901]: Failed password for invalid user test from 194.29.180.1 port 45058 ssh2
May 12 18:09:10 punk sshd[12903]: Invalid user test from 194.29.180.1
May 12 18:09:11 punk sshd[12903]: Failed password for invalid user test from 194.29.180.1 port 45458 ssh2
May 12 18:09:13 punk sshd[12907]: Invalid user test from 194.29.180.1
May 12 18:09:15 punk sshd[12907]: Failed password for invalid user test from 194.29.180.1 port 45801 ssh2
May 12 18:09:16 punk sshd[12909]: Invalid user test from 194.29.180.1
May 12 18:09:18 punk sshd[12909]: Failed password for invalid user test from 194.29.180.1 port 46145 ssh2
May 12 18:09:19 punk sshd[12911]: Invalid user test from 194.29.180.1
May 12 18:09:21 punk sshd[12911]: Failed password for invalid user test from 194.29.180.1 port 46579 ssh2
May 12 18:09:22 punk sshd[12915]: Invalid user test1 from 194.29.180.1
May 12 18:09:24 punk sshd[12915]: Failed password for invalid user test1 from 194.29.180.1 port 46941 ssh2
May 12 18:09:25 punk sshd[12917]: Invalid user test1 from 194.29.180.1
May 12 18:09:28 punk sshd[12917]: Failed password for invalid user test1 from 194.29.180.1 port 47274 ssh2
May 12 18:09:30 punk sshd[12921]: Invalid user test1 from 194.29.180.1
May 12 18:09:32 punk sshd[12921]: Failed password for invalid user test1 from 194.29.180.1 port 47755 ssh2
May 12 18:09:33 punk sshd[12923]: Invalid user test1 from 194.29.180.1
May 12 18:09:35 punk sshd[12923]: Failed password for invalid user test1 from 194.29.180.1 port 48116 ssh2
May 12 18:09:37 punk sshd[12925]: Invalid user test1 from 194.29.180.1
May 12 18:09:39 punk sshd[12925]: Failed password for invalid user test1 from 194.29.180.1 port 48528 ssh2
May 12 18:09:40 punk sshd[12929]: Invalid user test1 from 194.29.180.1
May 12 18:09:42 punk sshd[12929]: Failed password for invalid user test1 from 194.29.180.1 port 48940 ssh2
May 12 18:09:43 punk sshd[12931]: Invalid user test1 from 194.29.180.1
May 12 18:09:45 punk sshd[12931]: Failed password for invalid user test1 from 194.29.180.1 port 49272 ssh2
May 12 18:09:46 punk sshd[12935]: Invalid user test12 from 194.29.180.1
May 12 18:09:48 punk sshd[12935]: Failed password for invalid user test12 from 194.29.180.1 port 49620 ssh2
May 12 18:09:49 punk sshd[12937]: Invalid user test12 from 194.29.180.1
May 12 18:09:52 punk sshd[12937]: Failed password for invalid user test12 from 194.29.180.1 port 50052 ssh2
May 12 18:09:53 punk sshd[12939]: Invalid user test12 from 194.29.180.1
May 12 18:09:55 punk sshd[12939]: Failed password for invalid user test12 from 194.29.180.1 port 50441 ssh2
May 12 18:09:56 punk sshd[12943]: Invalid user test12 from 194.29.180.1
May 12 18:09:59 punk sshd[12943]: Failed password for invalid user test12 from 194.29.180.1 port 50777 ssh2
May 12 18:10:00 punk sshd[12945]: Invalid user test12 from 194.29.180.1
May 12 18:10:02 punk sshd[12945]: Failed password for invalid user test12 from 194.29.180.1 port 51245 ssh2
May 12 18:10:04 punk sshd[13088]: Invalid user test12 from 194.29.180.1
May 12 18:10:05 punk sshd[13088]: Failed password for invalid user test12 from 194.29.180.1 port 51768 ssh2
May 12 18:10:07 punk sshd[13092]: Invalid user test12 from 194.29.180.1
May 12 18:10:09 punk sshd[13092]: Failed password for invalid user test12 from 194.29.180.1 port 52042 ssh2
May 12 18:10:10 punk sshd[13094]: Invalid user test12 from 194.29.180.1
May 12 18:10:12 punk sshd[13094]: Failed password for invalid user test12 from 194.29.180.1 port 52433 ssh2
May 12 18:10:13 punk sshd[13097]: Invalid user test123 from 194.29.180.1
May 12 18:10:15 punk sshd[13097]: Failed password for invalid user test123 from 194.29.180.1 port 52790 ssh2
May 12 18:10:16 punk sshd[13100]: Invalid user test123 from 194.29.180.1
May 12 18:10:18 punk sshd[13100]: Failed password for invalid user test123 from 194.29.180.1 port 53213 ssh2
May 12 18:10:20 punk sshd[13102]: Invalid user test123 from 194.29.180.1
May 12 18:10:21 punk sshd[13102]: Failed password for invalid user test123 from 194.29.180.1 port 53631 ssh2
May 12 18:10:23 punk sshd[13106]: Invalid user test123 from 194.29.180.1
May 12 18:10:25 punk sshd[13106]: Failed password for invalid user test123 from 194.29.180.1 port 53992 ssh2
May 12 18:10:26 punk sshd[13109]: Invalid user test123 from 194.29.180.1
May 12 18:10:29 punk sshd[13109]: Failed password for invalid user test123 from 194.29.180.1 port 54354 ssh2
May 12 18:10:30 punk sshd[13111]: Invalid user test123 from 194.29.180.1
May 12 18:10:32 punk sshd[13111]: Failed password for invalid user test123 from 194.29.180.1 port 43142 ssh2
May 12 18:10:33 punk sshd[13115]: Invalid user test123 from 194.29.180.1
May 12 18:10:36 punk sshd[13115]: Failed password for invalid user test123 from 194.29.180.1 port 43514 ssh2
May 12 18:10:37 punk sshd[13117]: Invalid user test123 from 194.29.180.1
May 12 18:10:39 punk sshd[13117]: Failed password for invalid user test123 from 194.29.180.1 port 44062 ssh2
May 12 18:10:42 punk sshd[13121]: Invalid user test123 from 194.29.180.1
May 12 18:10:44 punk sshd[13121]: Failed password for invalid user test123 from 194.29.180.1 port 44511 ssh2
May 12 18:10:46 punk sshd[13123]: Invalid user test123 from 194.29.180.1
May 12 18:10:47 punk sshd[13123]: Failed password for invalid user test123 from 194.29.180.1 port 44970 ssh2
May 12 18:10:49 punk sshd[13127]: Invalid user tester from 194.29.180.1
May 12 18:10:51 punk sshd[13127]: Failed password for invalid user tester from 194.29.180.1 port 45656 ssh2
May 12 18:10:52 punk sshd[13129]: Invalid user tester from 194.29.180.1
May 12 18:10:54 punk sshd[13129]: Failed password for invalid user tester from 194.29.180.1 port 46389 ssh2
May 12 18:10:56 punk sshd[13131]: Invalid user tester from 194.29.180.1
May 12 18:10:58 punk sshd[13131]: Failed password for invalid user tester from 194.29.180.1 port 47313 ssh2
May 12 18:10:59 punk sshd[13135]: Invalid user tester from 194.29.180.1
May 12 18:11:01 punk sshd[13135]: Failed password for invalid user tester from 194.29.180.1 port 48349 ssh2
May 12 18:11:03 punk sshd[13137]: Invalid user tester from 194.29.180.1
May 12 18:11:05 punk sshd[13137]: Failed password for invalid user tester from 194.29.180.1 port 48808 ssh2
May 12 18:11:06 punk sshd[13141]: Invalid user tester from 194.29.180.1
May 12 18:11:08 punk sshd[13141]: Failed password for invalid user tester from 194.29.180.1 port 50355 ssh2
May 12 18:11:10 punk sshd[13143]: Invalid user tester from 194.29.180.1
May 12 18:11:12 punk sshd[13143]: Failed password for invalid user tester from 194.29.180.1 port 51561 ssh2
May 12 18:11:13 punk sshd[13147]: Invalid user tester from 194.29.180.1
May 12 18:11:16 punk sshd[13147]: Failed password for invalid user tester from 194.29.180.1 port 52074 ssh2
May 12 18:11:17 punk sshd[13151]: Invalid user tester from 194.29.180.1
May 12 18:11:19 punk sshd[13151]: Failed password for invalid user tester from 194.29.180.1 port 52734 ssh2
May 12 18:11:21 punk sshd[13153]: Invalid user testing from 194.29.180.1
May 12 18:11:23 punk sshd[13153]: Failed password for invalid user testing from 194.29.180.1 port 53390 ssh2
May 12 18:11:25 punk sshd[13157]: Invalid user testing from 194.29.180.1
May 12 18:11:27 punk sshd[13157]: Failed password for invalid user testing from 194.29.180.1 port 54480 ssh2
May 12 18:11:29 punk sshd[13159]: Invalid user testing from 194.29.180.1
May 12 18:11:31 punk sshd[13159]: Failed password for invalid user testing from 194.29.180.1 port 55064 ssh2
May 12 18:11:32 punk sshd[13163]: Invalid user testing from 194.29.180.1
May 12 18:11:35 punk sshd[13163]: Failed password for invalid user testing from 194.29.180.1 port 56007 ssh2
May 12 18:11:36 punk sshd[13165]: Invalid user testing from 194.29.180.1
May 12 18:11:38 punk sshd[13165]: Failed password for invalid user testing from 194.29.180.1 port 57514 ssh2
May 12 18:11:40 punk sshd[13167]: Invalid user testing from 194.29.180.1
May 12 18:11:42 punk sshd[13167]: Failed password for invalid user testing from 194.29.180.1 port 58104 ssh2
May 12 18:11:44 punk sshd[13171]: Invalid user testing from 194.29.180.1
May 12 18:11:46 punk sshd[13171]: Failed password for invalid user testing from 194.29.180.1 port 59021 ssh2
May 12 18:11:48 punk sshd[13173]: Invalid user testing from 194.29.180.1
May 12 18:11:50 punk sshd[13173]: Failed password for invalid user testing from 194.29.180.1 port 32829 ssh2
May 12 18:11:51 punk sshd[13177]: Invalid user testing from 194.29.180.1
May 12 18:11:54 punk sshd[13177]: Failed password for invalid user testing from 194.29.180.1 port 33646 ssh2
May 12 18:11:55 punk sshd[13179]: Invalid user test2 from 194.29.180.1
May 12 18:11:58 punk sshd[13179]: Failed password for invalid user test2 from 194.29.180.1 port 35415 ssh2
May 12 18:11:59 punk sshd[13183]: Invalid user test2 from 194.29.180.1
May 12 18:12:01 punk sshd[13183]: Failed password for invalid user test2 from 194.29.180.1 port 36602 ssh2
May 12 18:12:03 punk sshd[13185]: Invalid user test2 from 194.29.180.1
May 12 18:12:06 punk sshd[13185]: Failed password for invalid user test2 from 194.29.180.1 port 37427 ssh2
May 12 18:12:07 punk sshd[13189]: Invalid user test2 from 194.29.180.1
May 12 18:12:09 punk sshd[13189]: Failed password for invalid user test2 from 194.29.180.1 port 37983 ssh2
May 12 18:12:11 punk sshd[13193]: Invalid user test2 from 194.29.180.1
May 12 18:12:13 punk sshd[13193]: Failed password for invalid user test2 from 194.29.180.1 port 38463 ssh2
May 12 18:12:15 punk sshd[13195]: Invalid user test2 from 194.29.180.1
May 12 18:12:17 punk sshd[13195]: Failed password for invalid user test2 from 194.29.180.1 port 38895 ssh2
May 12 18:12:19 punk sshd[13201]: Invalid user test2 from 194.29.180.1
May 12 18:12:21 punk sshd[13201]: Failed password for invalid user test2 from 194.29.180.1 port 39448 ssh2
May 12 18:12:23 punk sshd[13203]: Invalid user test2 from 194.29.180.1
May 12 18:12:25 punk sshd[13203]: Failed password for invalid user test2 from 194.29.180.1 port 39851 ssh2
May 12 18:12:27 punk sshd[13207]: Invalid user guest from 194.29.180.1
May 12 18:12:29 punk sshd[13207]: Failed password for invalid user guest from 194.29.180.1 port 40236 ssh2
May 12 18:12:31 punk sshd[13209]: Invalid user guest from 194.29.180.1
May 12 18:12:33 punk sshd[13209]: Failed password for invalid user guest from 194.29.180.1 port 40720 ssh2
May 12 18:12:35 punk sshd[13212]: Invalid user guest from 194.29.180.1
May 12 18:12:37 punk sshd[13212]: Failed password for invalid user guest from 194.29.180.1 port 42707 ssh2
May 12 18:12:38 punk sshd[13215]: Invalid user guest from 194.29.180.1
May 12 18:12:41 punk sshd[13215]: Failed password for invalid user guest from 194.29.180.1 port 44052 ssh2
May 12 18:12:42 punk sshd[13217]: Invalid user guest from 194.29.180.1
May 12 18:12:44 punk sshd[13217]: Failed password for invalid user guest from 194.29.180.1 port 44501 ssh2
May 12 18:12:46 punk sshd[13221]: Invalid user guest from 194.29.180.1
May 12 18:12:48 punk sshd[13221]: Failed password for invalid user guest from 194.29.180.1 port 45483 ssh2
May 12 18:12:49 punk sshd[13223]: Invalid user guest from 194.29.180.1
May 12 18:12:52 punk sshd[13223]: Failed password for invalid user guest from 194.29.180.1 port 45841 ssh2
May 12 18:12:53 punk sshd[13227]: Invalid user guest from 194.29.180.1
May 12 18:12:55 punk sshd[13227]: Failed password for invalid user guest from 194.29.180.1 port 46294 ssh2
May 12 18:12:57 punk sshd[13229]: Invalid user adm from 194.29.180.1
May 12 18:13:00 punk sshd[13229]: Failed password for invalid user adm from 194.29.180.1 port 46745 ssh2
May 12 18:13:02 punk sshd[13244]: Invalid user adm from 194.29.180.1
May 12 18:13:04 punk sshd[13244]: Failed password for invalid user adm from 194.29.180.1 port 47248 ssh2
May 12 18:13:05 punk sshd[13246]: Invalid user adm from 194.29.180.1
May 12 18:13:07 punk sshd[13246]: Failed password for invalid user adm from 194.29.180.1 port 47644 ssh2
May 12 18:13:09 punk sshd[13248]: Invalid user adm from 194.29.180.1
May 12 18:13:11 punk sshd[13248]: Failed password for invalid user adm from 194.29.180.1 port 48175 ssh2
May 12 18:13:13 punk sshd[13252]: Invalid user adm from 194.29.180.1
May 12 18:13:16 punk sshd[13252]: Failed password for invalid user adm from 194.29.180.1 port 48636 ssh2
May 12 18:13:17 punk sshd[13254]: Invalid user adm from 194.29.180.1
May 12 18:13:19 punk sshd[13254]: Failed password for invalid user adm from 194.29.180.1 port 49103 ssh2
May 12 18:13:21 punk sshd[13258]: Invalid user adm from 194.29.180.1
May 12 18:13:23 punk sshd[13258]: Failed password for invalid user adm from 194.29.180.1 port 49575 ssh2
May 12 18:13:25 punk sshd[13261]: Invalid user adm from 194.29.180.1
May 12 18:13:27 punk sshd[13261]: Failed password for invalid user adm from 194.29.180.1 port 49998 ssh2
May 12 18:13:29 punk sshd[13267]: Invalid user adm from 194.29.180.1
May 12 18:13:30 punk sshd[13267]: Failed password for invalid user adm from 194.29.180.1 port 50518 ssh2
May 12 18:13:32 punk sshd[13269]: Invalid user service from 194.29.180.1
May 12 18:13:35 punk sshd[13269]: Failed password for invalid user service from 194.29.180.1 port 50854 ssh2
May 12 18:13:36 punk sshd[13271]: Invalid user service from 194.29.180.1
May 12 18:13:38 punk sshd[13271]: Failed password for invalid user service from 194.29.180.1 port 51350 ssh2
May 12 18:13:40 punk sshd[13275]: Invalid user service from 194.29.180.1
May 12 18:13:41 punk sshd[13275]: Failed password for invalid user service from 194.29.180.1 port 51752 ssh2
May 12 18:13:43 punk sshd[13277]: Invalid user service from 194.29.180.1
May 12 18:13:46 punk sshd[13277]: Failed password for invalid user service from 194.29.180.1 port 52127 ssh2
May 12 18:13:47 punk sshd[13281]: Invalid user service from 194.29.180.1
May 12 18:13:50 punk sshd[13281]: Failed password for invalid user service from 194.29.180.1 port 52607 ssh2
May 12 18:13:51 punk sshd[13283]: Invalid user service from 194.29.180.1
May 12 18:13:53 punk sshd[13283]: Failed password for invalid user service from 194.29.180.1 port 53116 ssh2
May 12 18:13:55 punk sshd[13286]: Invalid user service from 194.29.180.1
May 12 18:13:57 punk sshd[13286]: Failed password for invalid user service from 194.29.180.1 port 53526 ssh2
May 12 18:13:59 punk sshd[13289]: Invalid user service from 194.29.180.1
May 12 18:14:01 punk sshd[13289]: Failed password for invalid user service from 194.29.180.1 port 54038 ssh2
May 12 18:14:03 punk sshd[13291]: Invalid user service from 194.29.180.1
May 12 18:14:05 punk sshd[13291]: Failed password for invalid user service from 194.29.180.1 port 54374 ssh2
May 12 18:14:06 punk sshd[13295]: Invalid user user from 194.29.180.1
May 12 18:14:09 punk sshd[13295]: Failed password for invalid user user from 194.29.180.1 port 54849 ssh2
May 12 18:14:10 punk sshd[13297]: Invalid user user from 194.29.180.1
May 12 18:14:12 punk sshd[13297]: Failed password for invalid user user from 194.29.180.1 port 55240 ssh2
May 12 18:14:14 punk sshd[13301]: Invalid user user from 194.29.180.1
May 12 18:14:16 punk sshd[13301]: Failed password for invalid user user from 194.29.180.1 port 55753 ssh2
May 12 18:14:18 punk sshd[13303]: Invalid user user from 194.29.180.1
May 12 18:14:20 punk sshd[13303]: Failed password for invalid user user from 194.29.180.1 port 56183 ssh2
May 12 18:14:21 punk sshd[13305]: Invalid user user from 194.29.180.1
May 12 18:14:24 punk sshd[13305]: Failed password for invalid user user from 194.29.180.1 port 56598 ssh2
May 12 18:14:25 punk sshd[13309]: Invalid user user from 194.29.180.1
May 12 18:14:27 punk sshd[13309]: Failed password for invalid user user from 194.29.180.1 port 56709 ssh2
May 12 18:14:29 punk sshd[13311]: Invalid user user from 194.29.180.1
May 12 18:14:31 punk sshd[13311]: Failed password for invalid user user from 194.29.180.1 port 56833 ssh2
May 12 18:14:33 punk sshd[13315]: Invalid user user from 194.29.180.1
May 12 18:14:36 punk sshd[13315]: Failed password for invalid user user from 194.29.180.1 port 56956 ssh2
May 12 18:14:37 punk sshd[13317]: Invalid user user from 194.29.180.1
May 12 18:14:39 punk sshd[13317]: Failed password for invalid user user from 194.29.180.1 port 57301 ssh2
May 12 18:14:41 punk sshd[13321]: Invalid user ftp from 194.29.180.1
May 12 18:14:43 punk sshd[13321]: Failed password for invalid user ftp from 194.29.180.1 port 57638 ssh2
May 12 18:14:45 punk sshd[13323]: Invalid user ftp from 194.29.180.1
May 12 18:14:48 punk sshd[13323]: Failed password for invalid user ftp from 194.29.180.1 port 58430 ssh2
May 12 18:14:49 punk sshd[13327]: Invalid user ftp from 194.29.180.1
May 12 18:14:51 punk sshd[13327]: Failed password for invalid user ftp from 194.29.180.1 port 59228 ssh2
May 12 18:14:53 punk sshd[13329]: Invalid user ftp from 194.29.180.1
May 12 18:14:55 punk sshd[13329]: Failed password for invalid user ftp from 194.29.180.1 port 59931 ssh2
May 12 18:14:56 punk sshd[13331]: Invalid user ftp from 194.29.180.1
May 12 18:14:59 punk sshd[13331]: Failed password for invalid user ftp from 194.29.180.1 port 60267 ssh2
May 12 18:15:00 punk sshd[13335]: Invalid user ftp from 194.29.180.1
May 12 18:15:02 punk sshd[13335]: Failed password for invalid user ftp from 194.29.180.1 port 60894 ssh2
May 12 18:15:04 punk sshd[13337]: Invalid user ftp from 194.29.180.1
May 12 18:15:05 punk sshd[13337]: Failed password for invalid user ftp from 194.29.180.1 port 33304 ssh2
May 12 18:15:07 punk sshd[13341]: Invalid user ftp from 194.29.180.1
May 12 18:15:10 punk sshd[13341]: Failed password for invalid user ftp from 194.29.180.1 port 33583 ssh2
May 12 18:15:11 punk sshd[13343]: Invalid user ftp from 194.29.180.1
... repeat forever

```

I can't find an authorized connection.  Since then I've closed off the port until I can find more info.  Any ideas?

---

### Post by spiderbatdad on 2009-05-12
I would definitely recommend fail2ban as a means of  blocking ipaddress after 3 (or # by configuration) bad login attempts.

---

### Post by lazyart on 2009-05-12
They won't be able to get in anyway (the root account is disabled in Ubuntu).  But fail2ban is what you should use to turn away those attempts.

---

