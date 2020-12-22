# Ultimate Guitar Hack
Download any Guitar Pro file, including 'Official' and blocked/removed tabs

## Overview

What this exploit does is allow downloads on any interactive file on Ultimate Guitar (i.e. Guitar Pro, Tab Pro, 'Official' tabs). This exploit is pretty easy to perform; **you don't even need to be a paying subscriber to Ultimate Guitar's premium service**.

I just copied the HTML from a Guitar Pro file that I was able to download (i.e. user-submitted Guitar Pro files) and pasted it onto the desired tab's webpage I was wanting, and then I just replaced values where necessary. With this exploit you're able to download:

- 'Official' tabs (in quotes because sometimes this can be misleading; they're not *official from the artist*, they're made by the Ultimate Guitar team)
- Blocked tabs (tabs that are now restricted from being viewed, submitted, and, well, downloaded – until now)

People take lots of valuable time wanting to help other musicians learn a song, for it only to be taken down due to "copyright", even though it's not a direct copy and it's ones own interruption of a song. The artists that do this is my main motivation behind this exploit. Some of these artists include: **Rage Against The Machine** (so much for being anti-corporation and anti-censorship), **Dethklok**, **David Bowie**, **Protest The Hero**, **Polyphia**, **August Burns Red**, and plenty more.

As [EvandroJGC](https://www.ultimate-guitar.com/u/EvandroJGC) said on an [Ultimate Guitar news post a few years ago](https://www.ultimate-guitar.com/news/ug_news/thank_you_ug_community_you_helped_us_unblock_700_tabs_join_the_campaign_to_unblock_more.html#5139700):

> If the tab was made "by ear", without transcripting from a songbook, is [it] not allowed? This is in the tab rules of this site, right? Why these artirts *(sic)* would be against it? It's a free/amateur version. Right?



## The exploit


1. Open the desired tab (remember, it must be interactive: Official, or Guitar Pro)

1. Copy the following code:
    
    ```html
    <form action="https://tabs.ultimate-guitar.com/tab/download"><input type="hidden" name="id" value="_TAB_ID_HERE_"><button><span>Download Guitar Pro File</span></button></form>
    ```

    I removed all unnecessary code – styling – and changed a value – so it displays "**Download Guitar Pro File**" as a plain button. This code is not malicious, it's just inserting a button. If you have doubts, here is documentation for [form](https://www.w3schools.com/tags/tag_form.asp), [input](https://www.w3schools.com/tags/tag_input.asp), [button](https://www.w3schools.com/tags/tag_button.asp), and [span](https://www.w3schools.com/tags/tag_span.asp) HTML tags (see "Definition and Usage" section).

1. Open Inspect Element in your browser. Sorry, yes, you need to most likely use a desktop operating system to perform this; I'm not aware of any mobile web browsers that allow for HTML code injection.

1. Paste the code. It doesn't matter *where*, but where you paste it, that's where it's going to show. Therefore I recommend pasting after the `<head>` and before the `<body>` HTML tags. If you paste the code in the `<head>` tag, you won't see it. If you paste the code before the `<body>`, it will show at the top of the webpage. See below.

    Before pasting:

	```html
	<!DOCTYPE html>
	<html lang="en">
		<head >…</head>
		<body style="background-color: #111; margin: 0">…</body>
	</html>
	```

    After pasting: 

	```html
	<!DOCTYPE html>
	<html lang="en">
		<head >…</head>
		<form action="https://tabs.ultimate-guitar.com/tab/download">…</form>
		<body style="background-color: #111; margin: 0">…</body>
	</html>
	```
		
		
1. You may notice a "**Download Guitar Pro File**" button appear at the top of the webpage.

1. Open up the `<form>` tag. You should now see the following:

	```html
	<!DOCTYPE html>
	<html lang="en">
	    <head >…</head>
	    <form action="https://tabs.ultimate-guitar.com/tab/download">
		    <input type="hidden" name="id" value="_TAB_ID_HERE_">
		    <button>…</button>
	    </form>
	    <body style="background-color: #111; margin: 0">…</body>
	</html>
	```

1. Edit "`_TAB_ID_HERE_`" to match the tab's unique ID. This can be found in the URL. For example, if you wanted to download the 'Official' tab "*Killing In The Name*" by Rage Against the Machine ([direct link](https://tabs.ultimate-guitar.com/tab/rage-against-the-machine/killing-in-the-name-official-2238297)), the tab ID is 2238297.

1. Your HTML code should now look like this:

	```html
	<!DOCTYPE html>
	<html lang="en">
	    <head >…</head>
	    <form action="https://tabs.ultimate-guitar.com/tab/download">
		    <input type="hidden" name="id" value="2238297">
		    <button>…</button>
	    </form>
	    <body style="background-color: #111; margin: 0">…</body>
	</html>
	```

1. Click the "**Download Guitar Pro File**" button on the webpage. This will download a Guitar Pro 6 (`.gpx`) file, even with the artist and song name in the file title. This means, Guitar Pro 6 or Guitar Pro 7 is required. There are third-party tools that can convert `.gpx` files for more compatibility, such as `.gp3`, `.gp5` files.

## Troubleshooting

**The page reloads when I click "Download Guitar Pro File"**

Ensure your values are correct. The value in the HTML code must also match the page you're on, otherwise you'll be redirected.

## What's Next?

The exploit works perfectly as it is, but it's not very user-friendly. I don't know any form of scripting that so it can be created into an extension. For now, you have to manually do everything. If you're a developer, please open an [issue](https://github.com/noahmaranesi/ultimate-guitar-hack/issues) or alternatively fork this repository. **Please credit me, as – surprisingly – I'm the first person (to my knowledge) to actually achieve downloading 'Official' and blocked tabs. It took me a lot of time to write this up and share it with everyone.**
