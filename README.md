# Alfred Zendesk Search
_Opens in your existing Zendesk tab!_

This is an Alfred workflow for opening Zendesk searches in an existing Zendesk tab. While there are plenty of Alfred Zendesk workflows that perform searches and open tickets in Zendesk, they all seem to have one annoying flaw: They open a completely new Zendesk instance in a new browser tab each time, ignoring any existing Zendesk tab. This results in lots of extra tabs and makes it harder to keep track of Zendesk-related tickets, searches, etc.

This workflow solves this problem by using AppleScript and JavaScript to look for an existing Zendesk tab in Google Chrome and then uses that Zendesk instance to open a ticket or perform a search. 💥

## Supported Ticket Formats

You can easily open a ticket by typing or pasting in the ticket number, or a number of ticket URL formats. This is useful if you want to just copy/paste a full Zendesk ticket URL into Alfred and then have it open in your existing Zendesk tab.

### Ticket Number and Variations 

- `zd 88888`
- `zd #88888`
- `zd #88888-z`
- `zd 88888-z`

### Ticket URLs

- `zd http://vip-support.automattic.com/tickets/91559`
- `zd https://wordpressvip.zendesk.com/agent/tickets/90318`
- `zd https://href.li/?http://vip-support.automattic.com/tickets/91559`
- `zd https://href.li/?https://wordpressvip.zendesk.com/agent/tickets/90318`

## Other Searches

If you search for anything that doesn't match the above ticket number or ticket URL formats, the workflow performs a regular Zendesk search. This means that you can do any type of search you'd do right from within Zendesk. For example:

- `zd fatal error`
- `zd assignee:"Raam Dev" status:solved`
- `zd status:open priority:urgent`

## ⚠️ Requirements

Note that this workflow uses AppleScript and JavaScript and requires enabling a few things. 

1. Allow JavaScript from Apple Events: `Google Chrome -> View -> Developer -> Allow JavaScript from Apple Events`
2. Requires **Alfred 3** to have permission to control **Google Chrome** and **System Events** in `Security & Privacy -> Privacy -> Automation` (you'll get prompted for these permissions the first time you run the workflow). 
3. Finally, it assumes that your browser is "Google Chrome".

Note that this workflow also uses PHP and assumes that you have PHP installed at `/usr/bin/php`. 

## Initial Configuration

When you first install the workflow, you'll see a window like the one below that lets you configure the variables associated with this workflow:

![zendesk-search-alfred-setup](https://user-images.githubusercontent.com/53005/71024717-8f255c00-20d3-11ea-9cba-eff8a8d6d664.png)

- `zendesk_url`: This should be set to your full Zendesk instance URL, e.g., `https://wordpressvip.zendesk.com`. This allows you to open ticket numbers using `zd 102453`.

The next two variables are related to the workflow URL matching that lets you to copy a ticket URL and then open the ticket in your existing Zendesk tab (e.g., `zd http://vip-support.automattic.com/tickets/102894`). If you use multiple ticket URLs for the same Zendesk instance, you can use this to support all variations of your URL. 

- `domain_regex`: This variable should be set to the applicable domains, separated with a `|` (OR regex character), e.g., `zendesk|automattic`.
- `subdomain_regex`: This variable should be set to the applicable subdomains, separated with a `|` (OR regex character), e.g., `wordpressvip|vip-support`.

If you only use one domain for your ticket URLs, you can simply omit the `|` and supply the appropriate domain and subdomain (e.g., `zendesk` and `wordpressvip`, or whatever your ZD instance subdomain is). 

## How I Use This Workflow

I generally use this workflow in one of two ways: to open a Zendesk ticket number, or to open a Zendesk ticket URL. 

### Opening a Ticket Number

1. Double-click on a ticket number to select it (assuming it's not a link) and ⌘+C (copy)
2. Type ⌘+space (to open Alfred), `zd`+space, ⌘+V (paste URL), and hit Return/Enter

### Opening a Ticket URL

1. Right click on URL and click "Copy URL" 
2. Type ⌘+space (to open Alfred), `zd`+space, ⌘+V (paste URL), and hit Return/Enter

## Tips

- If you use more than one Google Chrome window instance (e.g., one for personal stuff and one for work), keep the non-Zendesk window minimized (⌘+M) to prevent this workflow from bringing to focus both Google Chrome windows. 

## Credits

- Props to [@trepmal](https://github.com/trepmal) for the initial inspiration to work on this project
- Props to [@pesla](https://github.com/pesla) for the AppleScript and JavaScript idea https://gist.github.com/pesla/6ed38b2fd17b1bfdf515
