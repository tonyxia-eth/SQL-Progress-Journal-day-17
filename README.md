# SQL-Progress-Journal-day-17

# Day 18: SQL Learning Journal — Task 7 (Medium → Hard Level)

Today I focused on mastering the *medium-to-hard tier* of Task 7 from CS50’s Moneyball project, which meant diving into conditional aggregation.

## 🎯 Key Skills Practiced
- JOINs with GROUP BY and aggregation
- Using `AVG()` with `ROUND()` to clean up output
- Filtering years with `IN (1999, 2000, 2001)`
- Applying `HAVING` to filter grouped results
- Ensuring players appeared in all 3 seasons using `COUNT(DISTINCT year) = 3`

## 🧠 New SQL Rules of Thumb

- Only use `GROUP BY` when using aggregation (e.g. `AVG`, `SUM`)
- Use `HAVING` to filter after aggregation
- Use `IN` to match any value in a list
- `COUNT(DISTINCT col)` counts unique entries in that column
- `ROUND(x, y)` to round numbers to y decimals
- Always order results with `ORDER BY`, use `DESC` for high-to-low
- Alias column outputs with `AS`, use quotes if alias has spaces

## ✅ Example Query from Today

```sql
SELECT players.first_name, players.last_name, 
       ROUND(AVG(salaries.salary), 2) AS "average salary"
FROM players
JOIN salaries ON players.id = salaries.player_id
WHERE salaries.year IN (1999, 2000, 2001)
GROUP BY players.id
HAVING COUNT(DISTINCT salaries.year) = 3
   AND AVG(salaries.salary) >= 8000000
ORDER BY "average salary" DESC
LIMIT 5;


🔁 Next Steps
More hard-level practice with HAVING and COUNT(DISTINCT)

Prepare for subqueries (next concept tier)
