# CogniLog + Supabase Database Integration

## ✅ Setup Complete!

Your CogniLog app now has a FREE cloud database!

### Database Credentials

**Project ID:** imqashtpvioalkoudmzc
**Supabase URL:** https://imqashtpvioalkoudmzc.supabase.co
**Table Name:** entries

### Database Columns

- `id` (int) - Auto increment
- `entry_date` (date) - Entry date
- `created_at` (timestamp) - Auto timestamp
- `content` (text) - Add this column
- `user_id` (text) - Optional, for future auth

### To Get Your API Key

1. Go to: https://supabase.com/dashboard/project/imqashtpvioalkoudmzc
2. Click: Settings > API
3. Copy the "anonkey" (public API key)
4. Add to your HTML as shown below

### Update Your App Code

Add this to your HTML `<head>` section:

```html
<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js"></script>
```

Add this JavaScript before closing `</body>`:

```javascript
// Initialize Supabase
const SUPABASE_URL = 'https://imqashtpvioalkoudmzc.supabase.co';
const SUPABASE_KEY = 'YOUR_API_KEY_HERE'; // Get from Settings > API
const { createClient } = window.supabase;
const supabase = createClient(SUPABASE_URL, SUPABASE_KEY);

// Save Entry Function
async function saveEntryToSupabase(entryDate, content) {
  try {
    const { data, error } = await supabase
      .from('entries')
      .insert([{ entry_date: entryDate, content: content }]);
    if (error) throw error;
    console.log('Entry saved to database:', data);
  } catch (err) {
    console.error('Error saving entry:', err);
  }
}

// Load Entries Function
async function loadEntriesFromSupabase() {
  try {
    const { data, error } = await supabase
      .from('entries')
      .select('*')
      .order('entry_date', { ascending: false });
    if (error) throw error;
    return data;
  } catch (err) {
    console.error('Error loading entries:', err);
    return [];
  }
}
```

## Next Steps

1. **Get API Key:** Go to Supabase dashboard > Settings > API, copy the "anonkey"
2. **Update Code:** Paste key into SUPABASE_KEY variable
3. **Modify Save Function:** Replace localStorage with saveEntryToSupabase()
4. **Update View Entries:** Use loadEntriesFromSupabase() to fetch data
5. **Upload to GitHub:** Commit changes to your repository

## Features with Database

✅ Cloud storage (never lose data)
✅ Access entries from any device
✅ Scale to thousands of entries
✅ Real-time updates (with subscriptions)
✅ Automatic backups

## Free Tier Limits

- 500MB storage
- Unlimited API calls
- Up to 50,000 rows
- Perfect for personal diary app!

## Support Links

- Supabase Documentation: https://supabase.com/docs
- JavaScript Client: https://supabase.com/docs/reference/javascript
- Table API: https://supabase.com/docs/guides/api/rest/creating-updating
