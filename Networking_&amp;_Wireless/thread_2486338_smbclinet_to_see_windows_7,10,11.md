---
title: "smbclinet to see windows 7,10,11"
date: 2023-04-26
forum: Networking &amp; Wireless
---

### Post by ulao3 on 2023-04-26
I have a home network running ubuntu as a server. My network is set up to use Samba WINS and does so quite well. All of the window boxes and see each other and share wonderfully. I want to get more in to linux so I'm staring to install a few linux desktops but I'm confused why this is such a hassle. No matter what I do the linux does not allow me to connect to the samba share. I'm told the password is wrong but its not.

1) do I need to install smb on any of the desktops or is smbclient enough?
2) does the smbclient use my samba server, do the settings effect the smbclient? 
3) when I connect to a share it asks for a password but does not accept it, it just asks again. I know my passwords... what can I check?

I added a few things to my smb.conf but I'm not sure this is even relevant if smbclient just works with windows directly. 

   server signing = auto
   ntlm auth = true

---

### Post by SeijiSensei on 2023-04-27
Did you create the separate Samba password database using the "[smbpasswd]("https://www.samba.org/samba/docs/current/man-html/smbpasswd.8.html")" tool? 

```
sudo smbpasswd -a your_user_name
```

You'll be prompted for the password.

"your_user_name" must match a Unix account that appears in the /etc/passwd file.

---

### Post by TheFu on 2023-04-27
Microsoft has been making closed source "standards" that work only with Microsoft products for 40 yrs now.  Don't confuse a MSFT standard with the standard used by the rest of the computing world.  For example, WINS is a MSFT standard, but not used by anyone else.  The rest of the world uses DNS or mDNS (via avahi/zeroconf).

Different versions of Windows support different versions of the samba/cifs protocol.  In Windows7 and later, Microsoft finally got serious about security and improved the defaults with each new OS release.  That means that the version of samba client to connect to each is different.  Win7 uses smb 2.1, for example, so you'll want to ensure that your samba server supports version 2.1 of the samba protocol and higher, but not lower.

So get the best help running a samba server, we need to see the smb.conf file as read by the smbd parser.  This can be generated using **testparm -s** on the samba server machine.  When posting, please include the exact command AND the output wrapped in forum code tags.

As SeijiSensei said, it is counter-intuitive, but well-known (except to noobs) that samba uses a mix of users from the OS and it's own password database.  Setting up the samba password data base is performed using the command, **sudo smbpasswd -a {username}**  That username is on the Unix side, not Windows, if they are different.

For example, my Unix username is tf, but on Windows, by username is TheFu.  I'd run **sudo smbpasswd -a tf** to add my user and set a samba password on the samba server.  

Whenever Windows and other OSes need authenticated connections, some compromised translation layer is supplied which often breaks what is expected on each side.  For example, Samba file permissions as seen by samba clients are restricted to what CIFS/Windows supports.  The full permissions that Unix support aren't available.  Sometimes, the permissions seen through samba client connections are in direct conflict with what the native storage shows.  smbd runs as root, so really all samba file transactions are likely to work regardless of the underlying permissions on the Linux file systems.  The first time I saw that, it was surprising.  Generally, Linux/Unix doesn't allow extra access if the local access doesn't allow it too. Samba is the exception.

BTW, did you setup a stanza in the smb.conf to specify which directory areas can be accessed by each user?  That's necessary too.  If nothing is setup, there won't be any access.

---

### Post by ulao3 on 2023-04-27
""your_user_name" must match a Unix account that appears in the /etc/passwd file." There are a few user names in that file? IS this on the linux samba server, or did you mean on the linux desktop?

---

### Post by ulao3 on 2023-04-27
So that means the answer to 
"2) does the smbclient use my samba server, do the settings effect the smbclient?"
is yes?

---

### Post by TheFu on 2023-04-27
> **ulao3 said:**
> ""your_user_name" must match a Unix account that appears in the /etc/passwd file." There are a few user names in that file?

There are exceptions, but in general, yes, that is true for a home setup.  In a business, LDAP would probably be used for centralized Unix account management. That's separate from Samba Accounts ... er ... as far as the smbpasswd file is concerned.

The /etc/passwd file is the normal local account user/password database.  You can learn what each field means by reading the correct manpage in section 5 of the manpages.  Do that with **man -s 5 passwd**

---

### Post by TheFu on 2023-04-27
> **ulao3 said:**
> So that means the answer to 
"2) does the smbclient use my samba server, do the settings effect the smbclient?"
is yes?

Well ... sorta.  If the client doesn't speak the same smb version that the server is configured to use, then they won't talk.  I think there's 1 setting in the smb.conf file that applies to a Linux samba/cifs client connection, but all the others are for the samba server.

Samba should generally be avoided, unless you have MS-Windows clients.  For all other computing devices, there are better options.

---

### Post by ulao3 on 2023-04-27
this is what I have, green lines work red do not. 
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAm0AAAHgCAYAAAD3zVolAAAgAElEQVR4Xu2dvbIkyValo14BBJRBgVtjGIaKUj0vcJu/kdCwq1ULCLcVlDFEbJRRugWE29q10ZCGv 4XmG4FdQzDqAaFUUaAV6g5eU5lnsjIiNzbI3fEXjv8uxK0R7ov/9Z293U8f rNx6f/DfwPAhCAAAQgAAEIQECawBtCm7Q/iIMABCAAAQhAAALPBAhtFAIEIAABCEAAAhAoQIDQVsAkJEIAAhCAAAQgAAFCGzUAAQhAAAIQgAAEChAgtBUwCYkQgAAEIAABCECA0EYNQAACEIAABCAAgQIECG0FTEIiBCAAAQhAAAIQILRRAxCAAAQgAAEIQKAAAUJbAZOQCAEIQAACEIAABAht1AAEIAABCEAAAhAoQIDQVsAkJEIAAhCAAAQgAAFCGzUAAQhAAAIQgAAEChAgtBUwCYkQgAAEIAABCECA0EYNQAACEIAABCAAgQIECG0FTEIiBCAAAQhAAAIQILRRAxCAAAQgAAEIQKAAAUJbAZOQCAEIQAACEIAABAht1AAEIAABCEAAAhAoQIDQVsAkJEIAAhCAAAQgAAFCGzUAAQhAAAIQgAAEChAgtBUwCYkQgAAEIAABCECA0EYNQAACEIAABCAAgQIECG0FTEIiBCAAAQhAAAIQILRRAxCAAAQgAAEIQKAAAUJbAZOQCAEIQAACEIAABAht1AAEIAABCEAAAhAoQIDQVsAkJEIAAhCAAAQgAAFCGzUAAQhAAAIQgAAEChAgtBUwCYkQgAAEIAABCECA0EYNQAACEIAABCAAgQIECG0FTEIiBCAAAQhAAAIQILRRAxCAAAQgAAEIQKAAAUJbAZOQCAEIQAACEIAABNJC249ffza8/fKHYXj31fDh 58PP3nyYu6/HdKi774Y3nz zdXc95hnN3z3gMkYEIAABCAAgZ0JENp2Bv48XJnQ9t3wxZvPh6d4Obz/9uPwi59mwGJMCEAAAhCAAAROBKRCWzeWENq6sZqJQgACEIAABKIIENqiSLb0Q2hrocWzEIAABCAAAQio3bRZn3P79o//avj89Dm46f/efzt8HL13Z352axKaPnzxZjh9xOz5f5O Tv/pO6N9sZJ /Hr47O2Xw1jx89uMw73PtP04fP3Z2 FmmqPP/k3Hu9I3anz31Yfh 5 fPi348r97XC5tLxCG9/Gb45M7nT5xOdy1uoY13TsW/G//N/HN5eoLcu51rFQIQAACEIAABMTeHr0b2p7dejd89eH74ZJDRqFofNi3hrbnWHMOcs 5bfT5raX/blTPJUhNQuBVwJoEsUXdo3leabv89/fDtx9/Mbx 5Ow1SHm4vGqa8B0FsrnPtF1eNw2UF2bXuq6D4WSsEWeCG1sTBCAAAQhA4JaA1Nuj90PbNFAs3x6tCm3jm6hzOBxeb8qagsTdtz9HN2njsGO9ZToT0JaC4dKt2i2XBS2XOrnzRQRDrxXAZ7/YsBD2WLgQgAAEIAABCFS6aVt6e3AmPKwNbS8Xbp/eKn339Bbh0/cmvzm9tznzluly8bwGocWgd6P59TXL39K8feb6bdH5UDvWec3lPw//49M3Q5fntxTaHHOcuaUzfTFu9liwEIAABCAAgZ4J1Llp2ym03XxG685nyeYLx/EzGedbs0vf858LWyrMSxic czcy2umb5dObiUnHS8HxaW5OOY43Aa7S2hbDMGeMNjzcmXuEIAABCDQMwFC26cf9p29kXrOP9dfcjCLZenzZ9cDvHxB4RzaFsPX/Gg3N3h3Xj8OZNefKXua2vunu8TnbxvMh7xxgJ3/LN29328jtJm1wgMQgAAEIACBBgKEtmloG30g/syx6fNsntB28/ao5 bK6eqN/te3TV9D22tIW/wywfNwj9y03X4ZouXt0SbmTjQ8BgEIQAACEKhMoMvQ5vmW5ik0/HL42cs/tTX91updx0dvdS7c0t0GpdEXApZu9qZh8O35SxILn2WbCY/z857/punLFO3PtC3eRM586/Y1NC5oXvlN3coLEO0QgAAEIAABL4FDhrbXnYedtv/Fbi1efV5oPT64f9l95CvEU9/oLAzefFxjdhc98ePUXEye rPf3C2utvt818Dm72Vmrmm5iLYfXy7DRM3fmCxN2f6BgF17l/W/aE7OazgvOv8RYyz0EAAhCAAASOTuCYoW38g6 z/yD9u HdDz 8fqbsdKd0 QHd5d8883zfnFgqXfaVusuom2mbdypy/1/E7b853a7Pxvf h33N/Sj/q arj3O21Lk7S/BXv0Rcn8IAABCEAAAnMEDhranqa69OH809uPf/bPoy8C/N7w95d/gcB 2 72hmipsBaC22n8//q/hjenfw1g9pup/n9h4GXkhXFm r7/mbJxP6OwNeF4e6vn17v4kyNnhM3f1GVRQwACEIAABPohkBba kHMTM8E7C8iwAoCEIAABCAAgSUChDZqYzcChLbdUDMQBCAAAQgckACh7YCmqk6J0KbqDLogAAEIQKACAUJbBZcOopHQdhAjmQYEIAABCKQQILSlYGdQCEAAAhCAAAQg0EaA0NbGi6chAAEIQAACEIBACgFCWwp2BoUABCAAAQhAAAJtBAhtbbx4GgIQgAAEIAABCKQQILSlYGdQCEAAAhCAAAQg0EaA0NbGi6chAAEIHJrAm//5/w49v7WT /gnv7b2pbwOAmEEwkIbC33eExZ6WK3SEQQgsAMB9nL28h3KjCFWEiC0rQTnfRmhzUuK5yAAAQUChDZCm0IdomGeAKFt48ogtG0MmO4hAIFQAoQ2QltoQdFZKAFCWyjO284IbRsDpnsIQCCUAKGN0BZaUHQWSoDQFoqT0LYxTrqHAAQ2JjAX2nr74xMGGxcZ3a8msGloY6EPQ28MVlciL4QABCQIEFiGAQYSpYiIGQKEtsCyYKEHwqQrCEAghQD7GKEtpfAY1EWA0ObC5HuIzc7HiacgAAFdAuxjhDbd6kQZoS2wBtjsAmHSFQQgkEKAfYzQllJ4DOoiQGhzYfI9xGbn48RTEICALgH2MUKbbnWijNAWWANsdoEw6QoCEEghwD5GaEspPAZ1ESC0uTD5HmKz83HiKQhAQJcA xihTbc6UUZoC6wBNrtAmHQFAQikEGAfI7SlFB6DuggQ2lyYfA x2fk48RQEIKBLgH2M0KZbnSgjtAXWAJtdIEy6ggAEUgiwjxHaUgqPQV0ECG0uTL6H2Ox8nHgKAhDQJcA RmjTrU6UEdoCa4DNLhAmXUEAAikE2McIbSmFx6AuAoQ2FybfQ2x2Pk48BQEI6BJgHyO06VYnyghtgTXAZhcIk64gAIEUAuxjhLaUwmNQFwFCmwuT7yE2Ox8nnoIABHQJsI8R2nSrE2WEtsAaYLMLhElXEIBACgH2MUJbSuExqIsAoc2FyfcQm52PE09BAAK6BNjHCG261YkyQltgDbDZBcKkKwhAIIUA xihLaXwGNRFgNDmwuR7iM3Ox4mnIAABXQLsY4Q23epEGaEtsAbY7AJh0hUEIJBCgH2M0JZSeAzqIkBoc2HyPcRm5 PEUxCAgC4B9jFCm251oozQFlgDbHaBMOkKAhBIIcA RmhLKTwGdREgtLkw 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 P7nw0 eWMz9t44R7Tp12O Km8GECBDadjTj6MFtbXg7vW7tbd/UPgLcjgXd0VCENi2zCW1afqBmPwKEtv1YP4 UGdys8aNvwdYGqKgA1zLfpTKI1LJzqTFcIAFCQiDMgK7wIwAiXZQkcKjQtnRIqx282cGtJcxEsFMIby1zvreSI3iU3Ck6F01I0CoA/NDyAzX7ESC07cf6aqTegtt58gS4pIJj2IcIeN8eHT/37R//1fD56XNw0/ 9/3b4 IufXv6rGUC2J48/k3l8/TffjizXD6f5//N nr9JM9qXQFy9bvTQu68 DN///PQpvvH/fhy /uztMDe98ef zq 4muMvh Fnb78crsm8H779 Ivhpz9 PXx203aa5sdhhOzm84RXTF7AvPR3M9k23Z6iaeN26nFBw jzkia3dfZvjN8M0zRMdcb/qO0PD6 U4PJ56JIUBoi G4qheF4HYS7g1SkbdM3jGnYCM1nPteq2WsbQtdq4qKF21CoDm0Pat4N3z14fvhkndGgWQchFpD23N8Oge505E9DjRL//0elYuu6eH/3fDFm8 fosEpL46C2zhYTUPjpe167pc5znC5bpuMdZnPQn/v3g3vfvhh J1ZBsv8b8Lugu67xdTK7RTXZr7Q8jzGiOnYz9fnX Z5CbqnEDYKv9NQe93nErtJ6Fqj4dOXcjZZdHQ6S4DQllwYKsEtK7y1jEuASy7WjodvD22TwPCJnbefK9STm7bznddr2Pk01vB6SzV/OzZv4OWmaObWbjZkXILU/A3P5TWj/m60ji/uFsLsi9rXG6HZoDsNrXc4vwZdv 57Jb a28yN2nXIetV3HWhvdSto6HhbSJk6oS0F /WgSsGtJURtcbu05tZrCx1nh9bo2SNcCpRtVxK8YWvNrdma15zhXw7t8dtlM HLFT6eH5oPmy1m3w1ts4HlfKM3P/Z5jk23k8PrLeHsLdTMhOZ0x3F7DZ/Lem6fuRt2T IWbiKfGi63pK/jbaShpTh49mEChLaHEcZ0QHDzB9l7xAlwMfVIL9cEVEPb HB yVwrPme08Dmy5c9KvbJZ jzX8xNzN23RoW0xoM7f0N2E3blC94beJm6vIcqzts4B9TW02Z9bu7pdnb2d3UqDZ0Y8E0WA0BZFMqAfteB2mpL3pkktLG2pp4VLVsAMKEe6GBHQDW2jz0lNglKzgYshZPpFgPsf5r98AUMutLXrdjH0cLvzzNwYN6HtThifq82528nx5 Y882rR4OmPZ2IIHC60LR2oWx/iMXbk/47b0jyqhrfTfLb23suGABe1SvbvRza0jb54cKbS8nm2RZI3/b6 dTm XZt7q0/t7dEzjzW6myttkVv727Wnsc23zp8FTt5evny2cfmLJd63jP0amknxgpUECG0rwW35MsUbt/N8vQFFNShtrWvpj4aWetlDY4senp0/PL1B7orfzNtW1sHs cbhKZj8cvjZyz 11fK5NOtbkzffKLz/tuPVIb/HTdvSXGRbtO92LtP8Bt7mdanseZ famVRtnfeMvJHz47b94qYObt3lHN41LbwE/oIF9Yh8ChLZ9ODePQnDzIfOGyGlvewWjtfrGevfS6iPe51PegGYesnOfNbr3bczx22pXb5HNH8Cvt0lLn4Ga rfwsx6vaeDlN IuvwVmHPwLPwdyn8sDX0Q46bx563D82a0zh3W6l6u9ldtTT6MgeXsbOtK35t 3HYXIdefhrkh4UvlGypoc tYfdZE9p2R 4fUDm4tdwo7RU61gYkdX0EOP a2erJTUPb6Jt 8/8g/aff6Bod5svhbBRYvB on3mLdcpx6ec2zrd6v/f3n3265Ru/cuanK6K/iGAYPvubZ8 veQk1lu673TdyO/U1/U262/6vw7b5R8Clg8nn9e54v52GrVYf/Y4JENrE68EKInsFjnuYLI3n1 6l1atnOqe99LUE3nvc99Qrvkw2l7dtaHs zWf/JYDnt7j 7J9f2p4Dz 8Nf3/5lwjs2xT/t0kXvlm48AH4pYP/JSSN 5qEo jQ9sTn8nbgVRUYv5M3qZgl3Tf/EMRNpbVxe3n5/GvmPovoD22nbj/9yxlP/6f9mbWNNGy EhmA0FagBqwQonB4Wxr3Dm7n8by6CHAFFgISIQABCHROgNBWpACs8KEQ3FpukDL0WgznSqGKzszQWWQJIRMCEIBAeQKHDG1L4SHjAI6sECt0KM3P0pp189YSLBWCkJfjvTpTqovI9UBfNoHf/Js/uDz0L3/4t/YLeAICEJAmQGiTtudWnHWIqx3Qlt7M8EaAK1b8yHURGAe16QtUgxvh0mUtD0FgILQVLAIrCBHc2k21mC71mMV6rd7xPLK0t7vDK 4RuBfSKoS2Of2ecEnQY130SIDQVtR169BWPJAtzdm3bufxvTqnpZPFfK1eAlzRxf8kuyWojWfpCUNTKluGo6V5WDrXBr26jqMcAi8ECG2FK8E6rLNChIXU0k14swjeb/fyvdeLau08Rqb2q9cGtfOsrSB0L6w9GvzmyD/yNu4WoW3LcFq78lCvRIDQpuTGCi3WAa18 FraVcLbSYdX69TCbP5rdY/nkT2HFcviMC/ZO6idwFljtoa/6MC2pPERXVuEwMMUIRORIkBok7JjnRjrYFY dC3tSsHtrMWrWS34rNGtFkLXrZBar7JCkzWbteHFO 7a/s 6H7lhu9fHI7oiNFm 0A6BCAKHDW1LtyPKAeYRQ60DWX3elv6jhLfTPBS88PK V5MK83hkzSi91huYljRvFVim4z0yjnWL19J39M2Yxb9Fm1JdoeV4BAhtB/P03mFc4ZD1hgm1uXh1q92 PXJ7qDqXKkvaCgrWPB4NEi3jPzpWZGBb6utRjRaPR/u3/KQdAh4ChDYPpWLPENzyDFsT3lRu36ICnNp88qrhdmQrGFhaI4JDi4Y9xlszRvRN25m7xWaNVstT2iHQQoDQ1kKr0LPVg9sJtTcAqd26PRp lObj9eDe0lCaT8YStoKApSkiKLRqiBjTul07ta8dZ6vQtqVmy2faIeAhQGjzUCr6zBGCG FNp/gIcH4vWkPStOe1YWbaT6uOqHH3CD9bBrc99PuriSch8EqA0HbwajhKcDtCeGuZw7Qs1W6rCHC3G0drQNoqqHkCx5Zje8aPCIdbh7a95nHwI4jpBRMgtAUDVeyO4KbnytrQoxbezmTXzmfsjOrc7lWPUlDzhIytw5pHQ0RgWxonqu8xJ8vjLcbU27FQpEKgu9B2Al/xcHi0YI4U3FpurCp4vTbwqM5t7XyqBDjrELfW6haHfKumLTRYgS16zD1u2s5eWnyj52bVEO39Ejh0aFs63FUPu63L8GjB7WjhrWU VQLOUQKcdWhba3erQ71V11Y69g5se960cetmVTftexIgtO1JW2AsgpuACQ4Ja8OO8h8ka eUFVBbA9HU1qyANFdeW2rJCGxZoc2a66l9a9aO7YNHDkyA0HZgc5emdsTg1nJLpRxs5jxbE3YqzHHNvLYOcMpBzRMYxnz2Cg9Z/wTUnm PTtelVSd7se/w Op yoS2TkvgqMGN8HZb0D0EuNOs18zTOnw928MeB3SLzj30nLlkBbbMmzbP3Llx86wcnllDgNC2htpBXnPk4Hbk8NYyt2mprgk2e5f7ozdwVoBrCUBLc98rGLVo3UuTJ7TsoSXzpm1cF5nBde 1yXj5BAht R6kKiC4veCvEGbmCmVtwKky37XzG7M6zbUl/Mxx3iOEeIPAVN/e2pZuuc669tKjEtosHty6pR5xhxuc0HY4S9sndPTg1nIzVSXMEODa6/z0it/9y99yv3Cv8FEprFkBZU9mSqHN4kJwcy87HjQIHD60LR3YlQ/nLaq6h BGeLtfOdXWRMQt3DTE7Rk6jhTWMkKJWmgjuG1xMtHnlAChjZq4EOgluPUS3lrmOV0GlQLc6fD hz/9p4dXcsacW962zQqUqmFEMbSpsnp4cdCBDAFCm4wVGkIIbrc ZBzmW1TDmpsp1bnfCzsVAlyVsKYeQlSDmzq3LfYX tyHAKFtH86lRukpuLXcRqkGmNbiWhPeTmNkz78l6JyZKAW4Vv2ZN2tnfpbmbI3KoY3g1roz8byHAKHNQ6nDZ3oLbj2Gt5Y5j5fAnuHNCg3W0hyHirVh9dG5t84hOwhVCWxLoUiFXyWO1jqiXYcAoU3HCzklBLdlS/YMLnsUxtpAswWH1pAz5eM9tNfO2RviWufh1b1HPVjaVbSq37QR3Pao1r7GILT15XfzbHsMbi03UFuElmaTgl wNsw8wsIKCdYUHw0Ra c8F Ba5/KodotNa3ulH4utEto84U2tDlrrhuf3IdBFaFs6hB85ZPaxR2OUXoMb4e3tqgL0rqvWcLP2Rq11EhEBzvN7cIqHdKXAdvK1Wmhb0jyuUcW6aF1DPL8dAULbdmwP1XPPwa338NYy/2nRTwOcalBbWqxbBDjVQ7laYKsa2ghuhzoad58MoW135HUHJLj5bp68N00VK2FtiPHcPC3xUAo5a c/nptifVQMbJVDG8Gt4u6noZnQpuFDGRW9B7eWWyfFwzmy0NYGGE AUwpqU2bngKP0cyKP Fo1sFUPbQS3R6q239cS2vr1fvXMCW4v6Lyh5ejhrYXFuOhU/gkp70Ko/oO c/OsHNiOENrOnlgfG1D I8a7fnguhgChLYZjd70Q3F4t7zm8TQ btbdPysHWOlDHi/90uHrr4d6msQeP6oHtSKGNW7fujtDVEya0rUbHCwlu/QW3lgCzJsDtEVa8K7dlrks3IaoB7giB7WihjeDmXZl9P9dNaFt6C0fpkKhYigS3a9e8h3SlumsJL3M1vCa8nfrJYtQy39a3rbz1sdUtnDW31vlk71kVf/LDYnY0j6z50t5GgND2bx/aiPH0DQGC221ReA/nrGBilbF1cFivj7552oNTy5wjwo23RqICnDW/iDlZdbFF xGDG7duW1TKMfoktBHaQiqZ4FY/uFmHulUoLYf 2sCyRXhrmXfLHC1e4/a1PMZ93GNjzXGrebUwWPvsUUMbwW1tRRz7dYQ2QltYhRPc5lF6D QtAollrnWYW6 POOy9fKZaHuXVMveIeVosz 1reSwFOGuee87Ny0M5CEEAACAASURBVKDluSOHNoJbSyX08SyhjdAWWukEt2Wc3sP40TBiGWod4tbrtzrkvXweCW tc99qrhbjyFu4e7 LpzC/FhZzzx49tBHcHq2QY72e0EZoC69ogtt9pN5wEhneWsPKdAZ7H 5eRt4A1zr/vefrXYRruYz7P4U41fl5OYyf6yG0EdzWVMYxX0NoI7RtUtkEt/zg1hpUsoPaErE1QeUceFsZVAoza7h4Q 4mm8JGnfYS2s74rJquVMMblcShu 0qtJ2cnNvoIm80Dl0tjZMjuNnAvAevt0atDd1SpLzhe1lN51j9n82yPFva1zyvGz/jrbHWfrd vrfQxq3b1hWl3T h7cmfqpuVdmm9qCO4 VzyBpK5Wj1yUIu8fZsLb8oh1Vc510 damHt7 JVDXA9hjaC25rVcYzXENoIbZtXMsHNj9gb3jy3R/dGPUpY8fKasjjiH2pL4f3oIa7X0EZw8rR3qS0EZo26WeCW5 zN4g0hrcjhLUxiTHB/bacHKEAHfvtnXsu7e27lWrGq eQ9vZJ u2/Yhr37 jHutJQhuhbbeKJri1ofYesEf/SYc5avcOqd7CmzewTTl660s9wBHaXhwiuLXtr1WfJrQR2natXYKbjXu6 XpDyDm8HfmvautgGtM9cVgbTNRuk5aqZm1gO1KAI7S9ummtjyPvDfbOeownCG2Ett0rmeB2i9zabL3BrUrYaC06i880rEWFEmWeUYFtzou1Yffc157cCG3XDlprheDWuvtoPU9oTHnpuMVgnkqCG42W9nzDnTW3izDiArrEUGEpU9wmISfSg/GuBOHmzNjuDW9odgdI3knCJ9jkpoI7SlVX5vwc06bD1GnDdb70G69WHp0bzmmRZWjxxAXo7jOWQytbg8wsLj0xpe03634Edom3cvu148NcUzbQQIbYS2tooJfvrowc3aND047x3E3kN0i4PSo731mRZekQHFy3GPALLEzGITycPj21pmWwRgQtuyY2p146ktnlkmQGgjtKWvj6MFN2uTtIC3Hr7ew1M5uLUwa Vj8Z62e3luET6qBLYIZpEBmNB2v8qt9bX1mmpdgzxPaLsiwD9lpbckqgc3a1O0iEdsmt6woRTeWrhFMLJ8GLd7eUaGjzl9FqO9uXgYrmW3NggT2mxXKtaRPav nujupu1kMaFNs9CtjV4pbJwIWpugRXmrw9bieNaVxbOV21acLH8UAtyW3xBtmf8jz3rr8d4YVq0S2vwOWetPYb35Z9Pfk4S2T55bm0J/pZEzY2uDz/bJ2vAsanttiBbHjODWym4vVpZnWeHtCIFtytZbl60BjtDWUsX2H5yKa69thsd9mtBGaJOrbmtj3zu4tYaNKdDMDdBiuUd4a WXyatlMXjZTvv01O8RA9uWAY7Q1lK5L89a67LKOmyfee1XENoIbZIVbB2InoPvkYlZG5rVt9qGZ/HcIry1MlRjZnl8bvey9Ya3HgLbFgFu s 5Va0nb91FPGetURhGUI7tg9A24rl1EIi17vi9WYdhtF/WBmYRr7DBWUwjwlsrxwrcLO jAlyPgW2OrbdO7/kSvT94a6Dic9RdHde6DG0ne/gyQo0itTbvRzfm1oAxpVYxcFhM1wa3VpYV2bWsGi/ncZ/T26Jz29FZ3eO6hqP3VrPFz6M/a63fnmtQyXtCGzdtSvU4q8XatFuDm7U5WUCOsnlZXL3hrZXnUfhZdfLo7ds5wPXGiwDnraz456y1TC3GM2/tkdBGaGutmZTnrYBhBTdrM7ImdeTNymK7FN5amB6Zn1U743Yva26KbKprWY57tvYNW8XxnrDWNWs513NCG6EttwIbRrc26ekGbG0 1tC9bU4W3zOvpbfw5nj2xtCqqUdv3wgZy4S99bvUA2xfyVh7J vau9LjnyO0Edriq2rDHq2NuSVQEDJuCVh8vcGNTf3 Ihgfiv/wp/ 0asUQMq6xRTDlFm6ZKfvlqmUa/qJuQ9uJJF9GCK nXTq0gkVrcCNgxIU3WNpLYOkWg/Bms7v3xNJvtVn7hWfUngMyt26eCtnvGULbhHXPi3O/snt8pNNGcu Qs4Ib4cL2wGLMrYTNcPqE9wBcGzR63r88P7C7lmvvte6t2/YVwStaCRDaCG2tNZPy/JrbCX5sc51VU9beG6CeA4OH9NqDb03Q6NELT2gb 7SG69TnnjivrV/P2uAZPwFCG6HNXy07P2ltEmc590JFT5vqo/ZYvAlv6wlbbD03v2tDRi9roDW0Td1cy7e3W7iIWl6/kngloY3QJrUKrA1hSSzBbb2NLcxP4cJ7uPUSFizy9/h6wtpc/14PegoUj4Y2buGsSn5tt/aMtXXtV9Dvk4S2Ge85bPZdENYGYKk5bxD3DjI8vabYynxuE/YGh57ZbxHYIsLFET2JDG0RjI8emK09hOBmnVzr2rsObSdkfIN0XeE8 iprwVv9L20IBLf75Fq5WxsvwW2Z99aBLertvaMEuK1CGwFuXY2fXmXtH9Y T/stAULbr7 9oXKUTUyt4FsDw1S/dwMguN0638rey/o8EuHNf5PZyrZ1HXu9mPZbfd/bI7RFBeVzP9WZn Zh7S1b13vr qj PKGN0LZpDVsL2hp87YInuL2QbeW/ljfh7bWS975hu7eGegpwGaGNWzhf3XPrZp10/nZCG6HNXy3OJ1uDwtobNUtOz8Gt1YNHw9raG4gj3DSM564U2CICRSV/skNbBO9xH5XYn3Vb 070PmOdAUdsJ7QR2kLq2lqs1iBbLebeglurD1txP/ntveWpeDjN1bNqYFsbqKevU/dJKbT1HOCsPWjLPcc6Z47Q3n1oWzpc1DcoheKzFqelca/F20Nwa/ViL/a9hLcqgS0iwCnvjVMf9qxza79rWQv3 lLmz42bpwoee4bQtnAjUGFhPGb9ule3hoPpKFmb6FGDW4sfWezPNXDEmzeLfzZz7yr3eqN6Z627bkw1ru4/6Uz6qjrA/vOtrjOUIboc2sM2vhWR2oHFxHCm4tnqjwb7lpUD6Ijn6bsCZIqPhVLbT18DaqtVcp7U/WWabQTmgjtM3WobXQrOJVXYjVg1uLL6oeHCG8WT4os7fWbuvNqNLtW XQduQA18N68a6rR58jtBHaLjVkLSyr2KocVBWDW4s3VXyoGt4sLyrxt9Z0tQB3lNB2xADX47rxrq W5whtC6HtBFHlyr/F0NZnrYVk9Vf1gKoS3Fr8qepFpfBm VHZA2utt/iUdft2xNB2tABX9Us7nvWxxzOEtk Ue/rnrKyDxyq8oxxMysGtxaMe/BjXZNYfU5YnR/HBWv/Kt29HD21Tb9Z8/jArUI/HZS15V9ntc4S2TkKbtUisEjrqgaQW3Fp86tGTrPDG7cDyDrE2OGwRvnsLbZVv4ay97qj7m3XWWu2EtoOGNmtBWIVxau9l0SgEtxa/8OW6erc4/L23Ar144dkvFN4 7Tm0VQxw1r7H uKmbXHvOcLbo9YC8Gy8vS6SjODW6hfe3K/gLcIbN2yeXWP mTU3cI96SGi79WKND3u hWrtg73ue0srj5u24jdtVsFbWy4L4pXQXsGt1TM8yvknsQhs1u7ha18bGtYEOEKb7claP849r/HFVjUM1r7IPvhCkdA2qqYqt21WcVsLhOJfJrRlcGv1DZ/W3xo8erAQ2KxdZF37msDQ4iWhrc2XNX5seQtn7ZHsiYS2q/pTDm1WMVtLlWK3CG1349bqHV7ZXnkPm5YD/zwqgc3m/ gTXv9aAwKhbb0zaz0Zj7hmvU0VW/tl7/sjN23CN21W8VrLs/fitvjca1/awFo2pVb/8KvNMe8hE UZ/rT5433a66M3wE3XHb55nfD94ertrWXdEdy8VLlpu5CyNo5HCtBvh/2 vtUXG5RFyN9uaVsOZnHPGktXbPY1hrmBu2CDfW9 H10Qpv3Lat92DulWt9ibiBW1qTPZ9z3LQZN22nZmuzf3SJtB7y0/F6LuBH2VuvH29YVh20 ohvFv22du/hMvXR8g2f2nyIeNrr5VyAI7RFOLDcx1pv1oY4/Lz2gtCWFNqsg8JadhwkFqH92lu8xLftffEeKqfwZnmHX9v7dW8Er5fTPn73L3/r6j/h4zY rvWnNcCN12nvXhLaJrW89i0xz5KwDgirj96L1eKzd3uLn3i3rzvew2R6uI9V4tm nlmjeT099zP2Fi8tuo 3t/ozN6L1bsbjKuv3QGjbOLS1HOxz5cRmo7nIvL7iX65/3oOEm5lcn1pH9/hKaGulGve8xx9rNALcPCFC2wahzXugLxUtB721nPPbLY/xMN jsQLPIXI 5PFOy7t7au75SmjT8dGz/u6pJcC90pENbW/evEmpuH//Tz 5GfdX/Pppbf OvfN5 598C//tHfPfR6z4s/fvzoeWzTZ7J8jZ7Ukt97 Didi4Kv0Xy36M86ODgYtqC X59jf7k53Y9760jWOlzqj/X5QobQNlMh4 B2L7BVCGrj6Skc7kcJbSeuY/8zwtrZW3z1HRtnv/7hT/9p9gWeP858I8U8peBrzEz27YVvG/p4K zFc5ckS rV1ueczj3WLKHNV9 Xp6oFNUJbo8EFH99jo7CwKBwA9zTOrdtxeFM8EBR8nWOq7rXSH1TWusn8w0vNRyvAKa7Rqb97rFlCm3dVTW5WGl42ZN7CENpanKr57B4bhUVG7QCY6lV6O9timXmQe7Spe 2Zg9ozGWtY2cdpgKsQ2E41tYePhLaG1dtyy6YS1AhtDQYXfXSPjcJCo3wATG9eznNRXKNq67XqTZtVr2rtGWtYfc2qeeTRs4ePpULbHkDuGVPpG4NzCzKb34mtqi7PglR4RpVfhQNA5TOI3jpSWK ENq9bjz2X4XWFNfsY1f1fvYePhLZGX6v8MnOlw32PQm 0WfZxfJW15iFhqr4S2h6y1f3ijD2wUs25Qe74YBY/QtuOJu85VFZBWXNU1WXpVmlX5aeqS8U3S0clfpW0Wtwz2lX4qejI8CBizCx hLYI9wT7yCooC4WqLku3SrsqP1VdKr5ZOirxq6TV4p7RrsJPRUeGBxFjZvEjtEW4J9hHVkFZKFR1WbpV2lX5qepS8c3SUYlfJa0W94x2FX4qOjI8iBgzix hLcI9wT6yCspCoarL0q3SrspPVZeKb5aOSvwqabW4Z7Sr8FPRkeFBxJhZ/AhtEe4J9pFVUBYKVV2WbpV2VX6qulR8s3RU4ldJq8U9o12Fn4qODA8ixsziR2iLcE wj6yCslCo6rJ0q7Sr8lPVpeKbpaMSv0paLe4Z7Sr8VHRkeBAxZhY/QluEe4J9ZBWUhUJVl6VbpV2Vn6ouFd8sHZX4VdJqcc9oV GnoiPDg4gxs/gR2iLcE wjq6AsFKq6LN0q7ar8VHWp GbpqMSvklaLe0a7Cj8VHRkeRIyZxY/QFuGeYB9ZBWWhUNVl6VZpV WnqkvFN0tHJX6VtFrcM9pV KnoyPAgYswsfoS2CPcE 8gqKAuFqi5Lt0q7Kj9VXSq WToq8auk1eKe0a7CT0VHhgcRY2bxI7RFuCfYR1ZBWShUdVm6VdpV anqUvHN0lGJXyWtFveMdhV KjoyPIgYM4sfoS3CPcE sgrKQqGqy9Kt0q7KT1WXim Wjkr8Kmm1uGe0q/BT0ZHhQcSYWfwIbRHuCfaRVVAWClVdlm6VdlV qrpUfLN0VOJXSavFPaNdhZ KjgwPIsbM4kdoi3BPsI sgrJQqOqydKu0q/JT1aXim6WjEr9KWi3uGe0q/FR0ZHgQMWYWP0JbhHuCfWQVlIVCVZelW6VdlZ qLhXfLB2V FXSanHPaFfhp6Ijw4OIMbP4Edoi3BPsI6ugLBSquizdKu2q/FR1qfhm6ajEr5JWi3tGuwo/FR0ZHkSMmcWP0BbhnmAfWQVloVDVZelWaVflp6pLxTdLRyV lbRa3DPaVfip6MjwIGLMLH6Etgj3BPvIKigLhaouS7dKuyo/VV0qvlk6KvGrpNXintGuwk9FR4YHEWNm8SO0Rbgn2EdWQVkoVHVZulXaVfmp6lLxzdJRiV8lrRb3jHYVfio6MjyIGDOLH6Etwj3BPrIKykKhqsvSrdKuyk9Vl4pvlo5K/CpptbhntKvwU9GR4UHEmFn8CG0R7gn2kVVQFgpVXZZulXZVfqq6VHyzdFTiV0mrxT2jXYWfio4MDyLGzOJHaItwT7CPrIKyUKjqsnSrtKvyU9Wl4puloxK/Slot7hntKvxUdGR4EDFmFj9CW4R7gn1kFZSFQlWXpVulXZWfqi4V3ywdlfhV0mpxz2hX4aeiI8ODiDGz BHaItwT7COroCwUqros3SrtqvxUdan4ZumoxK SVot7RrsKPxUdGR5EjJnFj9AW4Z5gH1kFZaFQ1WXpVmlX5aeqS8U3S0clfpW0Wtwz2lX4qejI8CBizCx hLYI9wT7yCooC4WqLku3SrsqP1VdKr5ZOirxq6TV4p7RrsJPRUeGBxFjZvEjtEW4J9hHVkFZKFR1WbpV2lX5qepS8c3SUYlfJa0W94x2FX4qOjI8iBgzix hLcI9wT6yCspCoarL0q3SrspPVZeKb5aOSvwqabW4Z7Sr8FPRkeFBxJhZ/AhtEe4J9pFVUBYKVV2WbpV2VX6qulR8s3RU4ldJq8U9o12Fn4qODA8ixsziR2iLcE wj6yCslCo6rJ0q7Sr8lPVpeKbpaMSv0paLe4Z7Sr8VHRkeBAxZhY/QluEe4J9ZBWUhUJVl6VbpV2Vn6ouFd8sHZX4VdJqcc9oV GnoiPDg4gxs/gR2iLcE wjq6AsFKq6LN0q7ar8VHWp GbpqMSvklaLe0a7Cj8VHRkeRIyZxY/QFuGeYB / Td/sKmqf/nDv13Vf1ahrxIr CJVfqq6BC2clVSJXyWtiv6r8FPRoeiRR1MWP0Kbx51iz2wd2PbAsTYU7qEtc4ysjcKas6ouS7dKeyV lbSq DvWYfHL2L//9Y/ 7lnix48fFZFJarJ83Eo0oW0rson9Ziz6LaZLcLulmrVRWP6q6rJ0q7SP f3GX/iqxFHedD/vwAh73fsntrJXPvPnmKjzEntpf5LQ1s5M/hWZCz8SDqHNF9pUD3n886 G80Gu6uXcTMbBjcO 3evxK878MvduQpvfw9OTWX oEtrafCrzdObij4LEoW HNvVDHg99q4HQ5uN0hKe4aTuCi4S2GxezUuwxymn7WWwdCjns5z2crgtC2/a1vscIhLY9KGuMYZ1tWt925NuTH114jlo7 ntie5aWvjVebprIKyAKnqsnSrtBPaVJyI1cFn2mJ5Kvemsgeq6FD26p62LH6EtqoVY jOKigLp6ouS7dK xw/1ds2bkv9VVNpXVTS6ndgvydV Kno2I987EhZ/AhtsT7K9JZVUBYAVV2WbpV2VX6qulR8s3RU4ldJq8U9o12Fn4qODA8ixsziR2iLcE wj6yCslCo6rJ0q7Sr8lPVpeKbpaMSv0paLe4Z7Sr8VHRkeBAxZhY/QluEe4J9ZBWUhUJVl6VbpV2Vn6ouFd8sHZX4VdJqcc9oV GnoiPDg4gxs/gR2iLcE wjq6AsFKq6LN0q7ar8VHWp GbpqMSvklaLe0a7Cj8VHRkeRIyZxY/QFuGeYB9ZBWWhUNVl6VZpV WnqkvFN0tHJX6VtFrcM9pV KnoyPAgYswsfoS2CPcE 8gqKAuFqi5Lt0q7Kj9VXSq WToq8auk1eKe0a7CT0VHhgcRY2bxI7RFuCfYR1ZBWShUdVm6VdpV anqUvHN0lGJXyWtFveMdhV KjoyPIgYM4sfoS3CPcE sgrKQqGqy9Kt0q7KT1WXim Wjkr8Kmm1uGe0q/BT0ZHhQcSYWfwIbRHuCfaRVVAWClVdlm6VdlV qrpUfLN0VOJXSavFPaNdhZ KjgwPIsbM4kdoi3BPsI sgrJQqOqydKu0q/JT1aXim6WjEr9KWi3uGe0q/FR0ZHgQMWYWP0JbhHuCfWQVlIVCVZelW6VdlZ qLhXfLB2V FXSanHPaFfhp6Ijw4OIMbP4Edoi3BPsI6ugLBSquizdKu2q/FR1qfhm6ajEr5JWi3tGuwo/FR0ZHkSMmcWP0BbhnmAfWQVloVDVZelWaVflp6pLxTdLRyV lbRa3DPaVfip6MjwIGLMLH6Etgj3BPvIKigLhaouS7dKuyo/VV0qvlk6KvGrpNXintGuwk9FR4YHEWNm8SO0Rbgn2EdWQVkoVHVZulXaVfmp6lLxzdJRiV8lrRb3jHYVfio6MjyIGDOLH6Etwj3BPrIKykKhqsvSrdKuyk9Vl4pvlo5K/CpptbhntKvwU9GR4UHEmFn8CG0R7gn2kVVQFgpVXZZulXZVfqq6VHyzdFTiV0mrxT2jXYWfio4MDyLGzOJHaItwT7CPrIKyUKjqsnSrtKvyU9Wl4puloxK/Slot7hntKvxUdGR4EDFmFj9CW4R7gn1kFZSFQlWXpVulXZWfqi4V3ywdlfhV0mpxz2hX4aeiI8ODiDGz BHaItwT7COroCwUqros3SrtqvxUdan4ZumoxK SVot7RrsKPxUdGR5EjJnFj9AW4Z5gH1kFZaFQ1WXpVmlX5aeqS8U3S0clfpW0Wtwz2lX4qejI8CBizCx hLYI9wT7yCooC4WqLku3SrsqP1VdKr5ZOirxq6TV4p7RrsJPRUeGBxFjZvEjtEW4J9hHVkFZKFR1WbpV2lX5qepS8c3SUYlfJa0W94x2FX4qOjI8iBgzix hLcI9wT6yCspCoarL0q3SrspPVZeKb5aOSvwqabW4Z7Sr8FPRkeFBxJhZ/AhtEe4J9pFVUBYKVV2WbpV2VX6qulR8s3RU4ldJq8U9o12Fn4qODA8ixsziR2iLcE wj6yCslCo6rJ0q7Sr8lPVpeKbpaMSv0paLe4Z7Sr8VHRkeBAxZhY/QluEe4J9ZBWUhUJVl6VbpV2Vn6ouFd8sHZX4VdJqcc9oV GnoiPDg4gxs/gR2iLcE wjq6AsFKq6LN0q7ar8VHWp GbpqMSvklaLe0a7Cj8VHRkeRIyZxY/QFuGeYB9ZBWWhUNVl6VZpV WnqkvFN0tHJX6VtFrcM9pV KnoyPAgYswsfoS2CPcE 8gqKAuFqi5Lt0q7Kj9VXSq WToq8auk1eKe0a7CT0VHhgcRY2bxI7RFuCfYR1ZBWShUdVm6VdpV anqUvHN0lGJXyWtFveMdhV KjoyPIgYM4sfoS3CPcE sgrKQqGqy9Kt0q7KT1WXim Wjkr8Kmm1uGe0q/BT0ZHhQcSYWfwIbRHuCfaRVVAWClVdlm6VdlV qrpUfLN0VOJXSavFPaNdhZ KjgwPIsbM4kdoi3BPsI sgrJQqOqydKu0q/JT1aXim6WjEr9KWi3uGe0q/FR0ZHgQMWYWP0JbhHuCfWQVlIVCVZelW6VdlZ qLhXfLB2V FXSanHPaFfhp6Ijw4OIMbP4lQptEaB77uPjx4/p058r9HRRxQWo qqgq4q1WQfAGj6VtK6Z39avUeGnomNr3lv1n8WP0LaVo4L9KhyihLb4wsDXeKYKPSr4Osch67BS8CRCgwo/9uIIN6/72GPNEtrifZPtcY CsibPRmERam/H13ZmFV6h4Ks3tFXgqawxw2v24viK2MNHQlu8b7I97lFQ1uTZKCxC7e342s6swisUfCW07VMpGV6zF8d7u4ePhLZ432R73KOgrMmzUViE2tvxtZ1ZhVco Epo26dSMrxmL473dg8fZUNbPE56hAAEtiLAARBPdo8DYI1qvF5D7f5rMrzGx5o EtrifaNHCEAAAoclwGEfb21GaIufBT3uQYDQtgdlxoAABCAAAQhAAAIPEiC0PQiQl0MAAhCAAAQgAIE9CBDa9qDMGBCAAAQgAAEIQOBBAoS2BwHycghAAAIQgAAEILAHAULbHpQZAwIQgAAEIAABCDxIgND2IEBeDgEIQAACEIAABPYgQGjbgzJjQAACEIAABCAAgQcJENoeBMjLIQABCEAAAhCAwB4ECG17UGYMCEAAAhCAAAQg8CABQtsTwB //mx4UPw/Duq HD9z8ffvIg1PHLz32/rD8P3PI3sOFHnArrbw9Lsv3gyffzOF9X749uMvhp8ekGGlKcX7/d3wxZvPh1u7vx0 /gK3VWsjvg6mMx3VxXtqIaoOQn377ovhze1GfS21sHeEti1D249fD5 9/XJ4ioNPeZDQFrXAPf2EbgIjH5fGxl PK9s9E n3pa9Fue Grz58P/A32HZ ru05sg5uNUyCfOGDfy3frV4X6Zu9fp9mUdg7QltoFf44fP3Z2 F0aTf9H4d6KOgdOxtv1NNbtWu/33/7ceASZkdrthhq/Ff6dGMfh/cNbuW3mA59RhGY2dsLH/xRVBT7Ob8jctT9mNAWWnWEtlCcAp29/tW2dLvy6jnBXMCwByVc3gJfCmWXUMfb4g iLvTyhX2d0Cbo4dmr496Glw5tX3/25uVWa2aDff380Yx5o7 mT2n8z/759jNt4 vab//4r4bP567PzEXLgd62qkebo4inlzpa9BqP2zweP63mt8NLQtt6uxdfqVYH10KvP8v6fvjqq/8zfHk6D8z9fwNUUl0q nZ Z S4f1SVDm3DZQOdBrPrzx5Mb0AugezTopt7P/36ffFJ/ 7PqjkOAalFKCBGzFMztI1q4ajX8ZtWhZjf9 d6/5DalNPROxetg6tz4NMfkk fgXn54lr3oe2pKNV8O /HJ6/ /B Ht5MvJBzh3ZDaoW14DWdXB b02yNXtzavG /5NfdD2/w1qDk4S29rNG3dPRjPiMU7u9N6/Q9nv2G8Mc1gG T7vQq4OrwDbyfPpH/wYwCnUp5pvnm6ND7bdOi4e2U9D/9DMMo0X1 kHEb4fh89PX9kdXpZeD9vW/3Q1t1mdb7n4gmdC2ZvfR9vQ0o8lnXPhQ hqbL69R9nv BWn7cQAACadJREFUZ15Olyx86eQh02deLFUHo8PfeqcmmkO1/pR8Gwftm1u1q0BX9 3T8qHt9Xr2bML5QH35/59 bOn5t7VubtXm/nIaHb7mTdq5AAht8XvMzeeGdDydHuIc3gH2C/s9 XTT6Lfbav 1HuBafBcqdTD5zPP0G HctE2sV/Ht9Of0jz8OP/nJnd9DPcDHWeqHtulbpG8//TbaOUydC o5pL29/CTH LDlpi1 /32sx8mVu4Knk2v3I3w24jGPIl8t6Pfi9Ea3rLxNGlkEpw9IXULx8/6ctO4vn1lzz673AK/hmn6 u/ 3WA0Pb6FunpIP3l8LPnD4leDtXx26Effnv4i cfu72 GiW0uXen3R4832gpeLr02ZbdYHQwkITfl73i/iFsfjmlA7 2mqJCHRDa2t1V8I3Q1u5b3isub1W f4pj3wzf/DDedEe/2/LV7zx9Vfv5vdKrf4qG0JZn3eLIKp4ufjtKkFllSRJ v94YLN k1v9LXbpMJOrgPiHeHp3ho Cb561PzzPSC2QYDnHTNr5Wf Y9 ZzZ9J 1mH4OidCmWKWTfzImxVMO6P0qQ8Hv0RebFr5hdvf3H/eDdeCRNOrgHmBC2xwdDd/ur8 RxsJfHjtIaBtvtk8FNf2sifGtEUKb5hlw9aH/FE8X/tHwBVx8zu2xOsr3 6R/ V81Gc OL6A85vW9V2vUwbJCQts8Gw3fPOu37jdHT QPE9pev0U693X80eE78 FhQtt2G/BDPd/9FtcOnjr ofjx/AhtD7k9 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[/IMG]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292128&stc=1[/IMG]

all the windows stuff that uses Samba and wins works fine. Win 7- win 11. they also see the server and each other ok. the only issue I have always had was that the server can not see the windows system. I recently added this linux desktop and I'm confused in general how this works. I get the version of Samba issues and the fact Windows is how it is. I expect issue with windows. but the confusion is how a linux box sees a windows share. Does any of the SMBclient need the SMB server that sits on the server. I would have imagines the SMBclinet alone can see the windows shares without a SMB.conf on that desktop. If SMBClient needs the SBM.confg, that impels that the linux desktop (not server) also needs Samba installed on it. that does not make sense to me because the server should have the SMB.conf not the desktop. I can not find the answers to understand how this stuff all works together. 



SMBClient:  makes a request to get a windows share. 
> does it look for smb.conf on the system that made the request?
> does it need to know what the samba server is so it can look up the info in smb.conf on the server?  -- If sop what files tells it the IP of the server?
> Does it not need to know about the SMB.conf and only communicate with windows.

---

### Post by ulao3 on 2023-04-27
ok so I need to analyze the entries and see what one is a samba element?

I see things like 
username:x:1000:1000:username,,, and a folder

Happy to look at a man page but I'm not sure what I'm looking for here?

---

### Post by ulao3 on 2023-04-27
> Well ... sorta.  If the client doesn't speak the same smb version that the server is configured to use, then they won't talk

but I do not want to talk to the sever I want to talk to the windows desktop? linux desktop to windows desktop.




> If the client doesn't speak the same smb version that  the server is configured to use, then they won't talk. --- I get that, and see how to set that in the SMBclinet. It must be 2 because I have mostly win7 boxes. 



> I think there's 1  setting in the smb.conf file that applies to a Linux samba/cifs client  connection, but all the others are for the samba server.--- I never told the SMBClient where the server is so how can it know?

maybe this?

SMB of TCP/IP or CIFS (Common Internet File System) uses: 
[TABLE]
[TR]
[TD]CIFS[/TD]
[TD]TCP[/TD]
[TD]445[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]CIFS[/TD]
[TD]UDP[/TD]
[TD]445[/TD]
[TD][/TD]
[/TR]
[/TABLE]
  Within SAMBAs smb.conf this can be controlled by: 
disable netbios = yes
smb ports = 445






> 
Samba should generally be avoided, unless you have MS-Windows clients.   For all other computing devices, there are better options.- Well yeah, I just want to access windows shares for my linux desktop. Most of the home is window, its just that way but the server is linux.

---

### Post by ulao3 on 2023-04-27
This is the smb.conf on the server.
```


[global]
   workgroup = renpet
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   log level = 3
   max log size = 1000
   panic action = /usr/share/samba/panic-action %d
   server role = standalone server
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   usershare allow guests = yes
   server signing = auto
   ntlm auth = true

#added things that are not default
wins proxy = yes
nt status support = yes
logon drive = l:
username map = /etc/samba/smbusers
interfaces = 127.0.0.1/8 192.168.0.0/24
wins support = true
server string = Samba file server
preferred master = yes
winbind cache time = 360
hosts allow = 127. 192.168.0.
passwd program = /usr/bin/passwd '%u'
remote announce = 192.168.0.255
disable netbios = no
time server = no
dns proxy = no
netbios name = ubuntuspawn






[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no


```

---

### Post by TheFu on 2023-04-28
Unix/Linux is case sensitive.  SMB.conf is not the same as smb.conf.  Always remember that.
If you want a Linux/Unix desktop to "find" any other system, then you need to setup mDNS or DNS or /etc/hosts files.  Period.  Put entries in the /etc/hosts files on the Linux desktop for all the Windows' share systems you want to be found.  It won't help you browse - that's been broken since Win10 when MSFT changed things, but it will make accessing the shares possible.  

There are other mDiscovery methods. I've never used them, but some others in these forums have outlined what is needed.
>  ok so I need to analyze the entries and see what one is a samba element?
No.  There isn't any "samba element" in those files beyond the username, but that same username needs to be put into the **smbpasswd** file.

> but I do not want to talk to the sever I want to talk to the windows desktop?
It is possible to have an smb.conf file without installing the samba server.  I wouldn't bother and I'd only create it when everything else has failed.  

I don't have any Linux samba clients that I recall.  Let me check quick. Ok, I found one.  It has these files in the /etc/samba/ directory:
```
-rw-r--r--   1 root root     8 May 24  2021 gdbcommands
-rw-r--r--   1 root root  8942 Apr  8 09:36 smb.conf
-rw-------   1 root root    31 Jul 14  2021 win7lap-D.credentials
```
The smb.conf file appears to be from the isntallation/upgrade.  I didn't add it.
No clue what gdbcommands is for. I've never touched it.
win7lap-D.credentials contains the login credentials for an old Win7 laptop to the storage their could be mounted using autofs.  I don't like to bother end-users with mount stuff.  OTOH, since it contains login credentials, the file can only be seen by the root account (for mount reasons).  Most storage in the Unix world is managed by admins, not end-users.  Mounts are setup by admins, not end-users, so I try to ensure that no end-users are involved in any mounts.  Network storage Unix mounts are server-to-server, not user-to-server, like with CIFS/Samba.  It is a different way of thinking, which I prefer.  Why should 50 users all need to mount the same storage 50 times to have access, when an admin can mount it once for all users, then have the standard file/directory permissions control who has access?

If you don't run the requested command to provide the requested data, it is hard for anyone to help. Inside a Linux file manager, have you tried entering //12.3.4.5/{sharename} to access the shared storage?  Use the IP address for each system.  

BTW, this is 1 reason why people use NAS devices. Much easier to have centralized storage that can be accessed by each system, in the best way for that system.  Linux would use NFS. Windows would use CIFS.

---

### Post by ulao3 on 2023-04-29
I learned a great deal guys thx, my problem was stupid, the SMB client just needed to know the workgroup, its not "workgroup"

---

### Post by TheFu on 2023-04-30
> **ulao3 said:**
> I learned a great deal guys thx, my problem was stupid, the SMB client just needed to know the workgroup, its not "workgroup"

Thanks for posting the answer.  No way would anyone here know what your workgroup/AD-Domain was.  I used a non-standard workgroup too, but since I seldom setup samba anymore (no need), I'd could miss that too.

To really help the community, please, please, use the "Thread Tools" button near the top and mark this thread as SOLVED, so the forum DB knows it and people can search that way.

---

### Post by mIk3_08 on 2023-04-30
> **ulao3 said:**
> I learned a great deal guys thx, my problem was stupid, the SMB client just needed to know the workgroup, its not "workgroup"
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

