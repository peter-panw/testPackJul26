
# Working with Custom Content

You can upload/download custom content via the demisto-sdk:



## Playbooks

### pcurrie_create_list.yml

This one simply creates a list, adds some IPs, removes some IPs. All of the scripts have `brand: Builtin` so there are no dependencies on Content Packs or other configurations.

<img width="420" height="1174" alt="pcurrie_create_list_Wed_Jul_08_2026" src="https://github.com/user-attachments/assets/49d5c6e0-087c-4487-b44b-3cc4f4be6427" />


## Jobs

There is no demisto-sdk for jobs, but there's a Jobs/ directory created by `demisto-sdk init` and some content packs on the marketplace I see do have jobs in there. To get a job we can use the REST API:

curl -X POST "https://api-pcsxsiam.xdr.us.paloaltonetworks.com/xsoar/public/v1/jobs/search" \
  -H "Authorization: PKvc66mrImtNPNIPbxEaUKByhurhyOpvrf0Ce4NViQSO5rRDskGpyowrUDs9N7VQjxsc460xosdPAREfyxkTVx638FzgedDPKSSKGKlbWSsfNAn8nXwOOhZvds7AICsL" \
  -H "x-xdr-auth-id: 466" \
  -H "Content-Type: application/json" \
  -d '{"page": 0, "size": 20, "query": "87bb5ddf-d0db-41a6-bafe-3f9d48fe07e5", "sort": [{"field": "id", "asc": true}]}'| jq


Included in the Jobs directory are a couple of examples:
. Time triggered

<details>
  <summary>Sample output</summary>

  ### Some JSON
  ```json
  {
  "total": 1,
  "data": [
    {
      "id": "87bb5ddf-d0db-41a6-bafe-3f9d48fe07e5",
      "version": 211,
      "cacheVersn": 0,
      "sequenceNumber": 1663475999,
      "primaryTerm": 21,
      "modified": "2026-07-09T07:55:02.167756837Z",
      "sizeInBytes": 2504,
      "sortValues": [
        "-9223372036854775808"
      ],
      "OWNER": {},
      "CustomFields": null,
      "account": "",
      "autime": 1783521167072717041,
      "type": "##default##",
      "rawType": "##default##",
      "name": "Test Job every 5 mins",
      "rawName": "Test Job every 5 mins",
      "status": 0,
      "custom_status": "",
      "resolution_status": "",
      "reason": "",
      "created": "2026-07-08T14:32:47.072717041Z",
      "occurred": "0001-01-01T00:00:00Z",
      "closed": "0001-01-01T00:00:00Z",
      "sla": 0,
      "severity": 0,
      "investigationId": "",
      "labels": null,
      "attachment": null,
      "details": "ghu",
      "openDuration": 0,
      "lastOpen": "0001-01-01T00:00:00Z",
      "closingUserId": "",
      "owner": "*@*.com",
      "activated": "0001-01-01T00:00:00Z",
      "closeReason": "",
      "rawCloseReason": "",
      "closeNotes": "",
      "playbookId": "a5b74d4d-5a48-4394-88b8-bb9717b9a643",
      "dueDate": "0001-01-01T00:00:00Z",
      "reminder": "0001-01-01T00:00:00Z",
      "runStatus": "running",
      "notifyTime": "0001-01-01T00:00:00Z",
      "phase": "",
      "rawPhase": "",
      "isPlayground": false,
      "rawJSON": "",
      "parent": "87bb5ddf-d0db-41a6-bafe-3f9d48fe07e5",
      "parentXDRIncident": "",
      "retained": false,
      "exported": false,
      "category": "job",
      "rawCategory": "job",
      "linkedIncidents": null,
      "linkedCount": 0,
      "droppedCount": 0,
      "sourceInstance": "",
      "sourceBrand": "",
      "canvases": null,
      "lastJobRunTime": "0001-01-01T00:00:00Z",
      "feedBased": false,
      "dbotMirrorId": "",
      "dbotMirrorInstance": "",
      "dbotMirrorDirection": "",
      "dbotDirtyFields": null,
      "dbotCurrentDirtyFields": null,
      "dbotMirrorTags": null,
      "dbotMirrorLastSync": "0001-01-01T00:00:00Z",
      "isDebug": false,
      "dedupID": "",
      "haIntegrationEventID": "",
      "haOriginalID": "",
      "incidentSchedulingKey": "",
      "startDate": "2026-07-08T14:31:54Z",
      "endingType": "never",
      "times": 0,
      "recurrent": true,
      "endingDate": "2026-07-08T13:39:04Z",
      "cron": "*/5 * * * *",
      "humanCron": {},
      "timezoneOffset": -60,
      "cronView": true,
      "timezone": "Europe/London",
      "scheduled": true,
      "scheduledEntryGuid": "",
      "minutesToTimeout": 0,
      "description": "",
      "currentIncidentId": "job-b2144775c12e47339635d9e883f9e0f8",
      "isCurrentIncidentManual": false,
      "lastRunTime": "2026-07-08T14:35:03.040380691Z",
      "nextRunTime": "2026-07-09T08:00:00Z",
      "displayNextRunTime": "2026-07-09T08:00:00Z",
      "disabledNextRunTime": "0001-01-01T00:00:00Z",
      "schedulingStatus": "enabled",
      "previousRunStatus": "idle",
      "tags": [],
      "shouldTriggerNew": false,
      "closePrevRun": false,
      "notifyOwner": false,
      "isFeed": false,
      "selectedFeeds": [],
      "isAllFeeds": false,
      "jobSchedulingKey": "xsoar-job-13e5c58c-f5d4-40c1-a3f2-9978d49d47b5"
    }
}
  ```
</details>

## Correlation Rule

I copied it from https://github.com/demisto/content/blob/4264d25829a6beaf5d5cc7eba8bbc18b8ba98b49/Packs/Dropbox/CorrelationRules/Dropbox_-_Massive_File_Downloads.yml#L4 as I could not download it from demisto-sdk download, and when I use the export and copy the file it did not like the formatting, but maybe i just pasted wrong? (Actually i think i just downloaded the json and named the file .yml that was probably it)


## Dashboard

Added a dashboard, downloaded from the UI, edit, upload.
