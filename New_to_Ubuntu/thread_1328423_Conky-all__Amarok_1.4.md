---
title: "Conky-all / Amarok 1.4"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by merlin_ie on 2009-11-16
Hey all. I was running an Amarok script in previous conky, but ever since I´ve installed conky-all deb (to get the cairo settings) the following code doesn´t work 

```
$color$stippled_hr${if_running amarokapp}
${color}${alignc}Now Playing${color white}
${alignc}${execi 10 ~/.conky/amarok artist}
${alignc}${execi 10 ~/.conky/amarok title}
${execibar 1 ~/.conky/amarok progress}
${alignc}"${execi 10 ~/.conky/amarok album}"
${alignc}${execi 10 ~/.conky/amarok year} - ${color white}${alignc}${execi 10 ~/.conky/amarok genre}
$color$stippled_hr
${alignc}Collection Information
Artists: ${color white}${execi 10 ~/.conky/amarok totalArtists} $color${alignr}Compilations: ${color white}${execi 10 ~/.conky/amarok totalCompilations}$color
Albums: ${color white}${execi 10 ~/.conky/amarok totalAlbums} $color${alignr}Genres: ${color white}${execi 10 ~/.conky/amarok totalGenres}$color
Tracks: ${color white}${execi 10 ~/.conky/amarok totalTracks}
$color$stippled_hr
${alignc}Collection Statisctics
Most songs by ${color white}${execi 10 ~/.conky/amarok most_songs_by_artist} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_by_artist_n}${color})
Most songs are ${color white}${execi 10 ~/.conky/amarok most_songs_are_genre} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_are_genre_n}${color})
Most songs during ${color white}${execi 10 ~/.conky/amarok most_songs_during_year} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_during_year_n}${color})
Most albums by ${color white}${execi 10 ~/.conky/amarok most_albums_by_artist} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_by_artist_n}${color})
Most albums are ${color white}${execi 10 ~/.conky/amarok most_albums_are_genre} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_are_genre_n}${color})
Most albums during ${color white}${execi 10 ~/.conky/amarok most_albums_during_year} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_during_year_n}${color})$endif
```

Note, this is not my EXACT code, this is one I found on goggle, but it´s pretty similar. I´m running Jaunty. Is there a way to fix this? Any help would be greatly appreciated

---

