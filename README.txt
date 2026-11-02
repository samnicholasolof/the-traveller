THE TRAVELLERS' COMPANION, VERSION 1.0
Set-up guide for Cupboard of Shame

Suggested address: https://traveller.cupboardofshame.com

WHAT'S IN VERSION 1.0
The app opens on a short welcome to the game and its world, then has
four tabs, in this order:
- Welcome: the world, how it plays, who you play, what you need, and
  how a game night runs.
- Rules: the core rules, plus the rules PDF to download.
- Play: party builder, mission generator and galaxy map, tarot, Trading
  Post and table tracker.
- Lore: the story so far, from Husk to Children of a Drowned God, plus
  photos from the table. You can log in and add new episodes.
The rogues' gallery is switched off for now. Its data is kept in the
app, ready for a later version.

THE FILES
index.html             the app (art, fonts and photos built in)
The-Traveller-Core-Rules-v1.0.pdf   the rules, for download and printing
lore/story.json        the story so far: this is what you edit
images/uploads/        photos you add while editing the lore
admin/                 the editing dashboard (Decap CMS)
admin/config.yml       dashboard settings: put your GitHub details here
sw.js                  keeps an offline copy on players' devices
manifest.webmanifest   home-screen app settings
*.png                  icons
_headers               tells Netlify to always serve the newest version


====================================================================
ROUTE A: QUICK START (NETLIFY ONLY, NO LOGIN)
====================================================================
Good for a first test. Editing the lore means editing lore/story.json
by hand and uploading the folder again.

1. On a computer, unzip the download.
2. Log in to Netlify, go to https://app.netlify.com/drop
3. Drag the whole "the-traveller" folder onto the page.
4. Open the .netlify.app link it gives you and check everything works.
5. To update later: open the site in Netlify > Deploys, and drag the
   new folder onto that page. (Don't use the Drop page again: that
   makes a separate, new site.)


====================================================================
ROUTE B: WITH LOGIN TO ADD LORE (GITHUB + NETLIFY), RECOMMENDED
====================================================================
The app's files live on GitHub. Netlify publishes them. You log in at
/admin to add episodes and photos, and the site updates itself about a
minute later. Free.

STEP 1: PUT THE FILES ON GITHUB
 a. Create a free account at https://github.com if you don't have one.
 b. Click New repository. Name it: the-traveller
    It can be Public or Private.
 c. On the new repository's page, choose "uploading an existing file".
    Drag in everything INSIDE the "the-traveller" folder, so that
    index.html sits at the top level, not inside another folder.
    (If the images/uploads folder doesn't upload because it's empty,
    that's fine.) Click Commit changes.

STEP 2: TELL THE DASHBOARD WHERE YOUR FILES ARE
 a. On GitHub, open admin/config.yml and click the pencil to edit.
 b. Change this line:
       repo: YOUR-GITHUB-USERNAME/the-traveller
    to your own GitHub username, for example:
       repo: samolof/the-traveller
 c. Commit changes.

STEP 3: CONNECT NETLIFY TO GITHUB
 a. In Netlify: Add new site > Import an existing project > GitHub.
 b. Allow Netlify to see the the-traveller repository and pick it.
 c. Leave the build command empty. Publish directory: leave empty or
    put a single full stop (.). Deploy.
 d. From now on, every change on GitHub publishes automatically.

STEP 4: ADD YOUR OWN ADDRESS
 a. In Netlify: Domain management > Add a domain >
    traveller.cupboardofshame.com
 b. Netlify shows a CNAME record. In Squarespace:
    Settings > Domains > cupboardofshame.com > DNS > Add record.
      Type: CNAME   Host: traveller   Data: your-site.netlify.app
 c. Wait up to a day (usually under an hour). Netlify switches on the
    secure https padlock by itself. Your Squarespace site isn't affected.

STEP 5: SWITCH ON THE LOGIN
 a. On GitHub: your profile picture > Settings > Developer settings >
    OAuth Apps > New OAuth App.
      Application name:           The Traveller lore editor
      Homepage URL:               https://traveller.cupboardofshame.com
      Authorization callback URL: https://api.netlify.com/auth/done
    Register it. Copy the Client ID. Generate a client secret and copy it.
 b. In Netlify, open your site: Site configuration > Access & security >
    OAuth > Install provider > GitHub. Paste the Client ID and secret.

STEP 6: ADD LORE
 a. Go to https://traveller.cupboardofshame.com/admin
 b. Log in with GitHub.
 c. Open Lore > The story so far. Add an act, or add an episode to an
    act: label, title, status (told, coming soon or side tale), the
    story, a photo, tales and quotes, and tags for people and places.
    Add game photos under "From the table".
 d. Click Publish. The site updates about a minute later.

WHO CAN LOG IN
Anyone with write access to the GitHub repository. To let a co-GM add
lore, add them as a collaborator: on GitHub, the repository > Settings >
Collaborators.


====================================================================
FOR PLAYERS
====================================================================
iPhone and iPad: open the link in Safari, tap Share, then "Add to Home
Screen". It gets its own icon, opens full screen, and works with no
signal once it has been opened once.

Parties, gear, XP and the chronicle save on each player's own device.
The home-screen app keeps its saves separately from Safari.
