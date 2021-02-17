To host a repository containing packs and/or events and delivering it to the launcher we have to do multiple step i want to summarize here. It will allow you to offer the content for events in the launcher (without beeing a computer scientist) and people can manage it (download/activate and deactive) it with one click.
A detailed documentation of the launcher can be found here: <https://re-volt.gitlab.io/rvgl-launcher/>

**1.** Sign up on `<https://github.com/>` (you have to upload a  .json file anywhere. So if you know how to do this without github, choose your way ;) )
**2.** Create a *new Repository* A repository is just a project where we can upload our source code or our json in our case. What a json is we'll see later.
**3.** Create a file called *repository.json* (you can give it a name you like but make sure its a .json file. Windows often think its more clever than you and make a new file a xxx.json.txt. Right click - properties shows you the real file extension. If its still a txt follow this <https://support.winzip.com/hc/en-us/articles/115011457948-How-to-configure-Windows-to-show-file-extensions-and-hidden-files> guide to allow showing file extension)
**4.** Fill your json with content. Open your .json file by right-clicking and open with editor (if you are more experienced choose any editing tool you like. Notepad++ makes live easier here) (A complete example with one pack and one event kann be found here)
**4.1** Add a repository name and version to your json. A version number can be `xx.xxxx`. Most common is the date you least updated your repository. The launcher will automatically check is this number is increased, if you restart the launcher. So you can deliver updates to packs easily.
```
{
   "name":"Maxi Stock repo",
   "version":"21.0217"
}
```
Now you have a repository. Keep care you ever have exactly the same amount of `{` like `}` 
**4.2**(Optional: Only if you want to provide a packs or multiple content packs): Add a `,` behind `"version":"xx.xxxx"` to let json know that there is more to read.
In a new line copy the **packages** block below. Also if you only want to add one pack, you have to copy the whole block. Do not skip the packages in the top line and do not miss any `{ }`
Now fill the field with your values. Description is simply a description of whats in your pack, version again is important to keep users on track of updates. The url is the url of your content pack download. You can host it anywhere you like. For example on dropbox, BUT make sure, your download link directly starts the download when clicking on it. You pack has to be zipped (not rar not whatever) On Dropbox you can ensure this with changing the `dl=0` to `dl=1` in the link.
 `<https://www.dropbox.com/s/h3b5f1dvvca3w0b/levels.zip?dl=0>` --> `<https://www.dropbox.com/s/h3b5f1dvvca3w0b/levels.zip?dl=1>`
The file must be the name of the zip file. Not so complicated isnt it.
(More experienced users also add the SHA256 checksum of the zip in a extra checksum field)
```
"packages":{
      "Stock Track Pack":{
         "description":"Test pack containing the stock tracks",
         "version":"21.0217",
         "url":"https://www.dropbox.com/s/h3b5f1dvvca3w0b/levels.zip?dl=1",
         "file":"levels.zip"
      }
   }
```
If you want to add a second pack, just add a comma after the `}` of your pack and copy the pack part. Than it should look like: <https://raw.githubusercontent.com/vonunwerth/re-volt-json/main/doublepack.json> (but not with two same packs, this would be a bit useless, wouldn't it?)
Your json should now look like: <https://raw.githubusercontent.com/vonunwerth/re-volt-json/main/test.json>
**4.3** (Optional: Only if you want to provide an event or multiple events):
On the same way we did it for packs, we add add events:
```
  "events":{
      "eventno1":{
         "title":"Event 1",
         "date":"17-02-2021 18:00",
         "hosts": {"Max":"192.168.178.20", "Wusel":"192.168.178.2"}
      }
```
Make sure you have a comma after packages, before theres the events block.
Give you event an id. In the example *eventno1*, than give it a proper title, add the date and add the hosts like shown in the example. If there is only one host, there have to be only one host ;)
